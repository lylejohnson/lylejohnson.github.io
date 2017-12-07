---
id: 5
title: Private Methods in C++ and Ruby
date: 2003-12-09T15:37:34+00:00
author: Lyle
layout: post
guid: http://lylejohnson.name/wp/?p=5
permalink: /2003/12/09/private-methods-in-c-and-ruby/
categories:
  - Ruby
---
I&#8217;ve recently had to re-learn the meanings of protected and private accessibility for [Ruby](http://www.ruby-lang.org) methods, and how those meanings differ from the same keywords in C++, and so I thought I&#8217;d summarize what I&#8217;ve learned here. Note that to keep things as simple as possible, I&#8217;m ignoring the exceptions to these rules for C++ that `friend` classes introduce.

First, the good news. As far as I can determine, everything that you know about _protected_ member functions in C++ classes applies to protected methods in Ruby classes. That is to say, a protected method can be called from other methods in the same class, as well as from methods in derived classes. Also, one instance of a class can call protected methods on other instances of the same class.

There are some subtle differences, however, when it comes to private member functions and methods. In C++, a _private_ member function can only be called from member functions of the class in which it&#8217;s declared. So if you declare a private member function `foo()` in a base class: 

<pre class="code"><code>
    class Base {
    private:
        void foo();
    };
</code>
</pre> then other member functions in 

`Base` can call `foo()`: 

<pre class="code"><code>
    class Base {
    private:
        void foo();
    public:
        void spam() {
            foo(); // this is allowed since spam() is declared in the same class as foo()
        }
    };
</code></pre> but 

`foo()` is **not** visible to classes derived from `Base`: 

<pre class="code"><code>
    class Derived : public Base {
    public:
        void bar() {
            foo(); // this should generate a compile-time error
        }
    };
</code></pre> This brings us to the first difference between private member functions in C++ and private methods in Ruby, and it has to do with the visibility of private methods in derived classes. As we&#8217;ve just seen, C++ private member functions are not visible in derived classes. In Ruby, however, private methods 

**are** visible in derived classes, i.e. if `foo` is declared private in the base class: 

<pre class="code"><code>
    class Base
    private
      def foo; end
    end
</code></pre> then methods in the derived class can call it: 

<pre class="code"><code>
    class Derived &lt; Base
      def bar
        foo # this is allowed in Ruby
      end
    end
</code></pre> The next difference between private member functions in C++ and private methods in Ruby has to do with the objects on which the private member function (or method) can be called. In C++, you can call a private member function on any instance of the class that declares that member function, e.g. 

<pre class="code"><code>
    class Base {
    private:
        void foo();
    public:
        void spam(Base *otherObject) {
            foo();              // this is allowed
            otherObject->foo(); // and so is this
        }
    };
</code></pre> In Ruby, you can&#8217;t specify the receiver when calling a private method. Put another way, you can only call a private method on 

`self`, either implicitly or explicitly, e.g. 

<pre class="code"><code>
    class Base
    private
      def foo; end
    public
      def spam(otherObject)
        foo             # this is allowed in Ruby (self is implicit)
        self.foo        # so is this
        otherObject.foo # but this isn't
      end
    end
</code></pre> In C++, one would choose the 

`private` access over `protected` access for a member function to better enforce data hiding: the less that derived classes &#8220;know&#8221; about the base class implementation, the better. In Ruby, however, there doesn&#8217;t seem to be any direct way to hide base class methods from derived classes. One person summed up the distinctions by saying that in C++, &#8220;private&#8221; means &#8220;private to this class&#8221;, while in Ruby it means &#8220;private to this instance&#8221;.