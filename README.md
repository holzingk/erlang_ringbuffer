erlang-ringbuffer
=====

Provides a simple fixed size queue using the [Erlang queue Module](http://erlang.org/doc/man/queue.html).

````erl
Eshell V8.3.5.1  (abort with ^G)
1> B = erlang_ringbuffer:new(3).
{ringbuffer,3,0,{[],[]}}
2> B1 = erlang_ringbuffer:add(eins, B).
{ringbuffer,3,1,{[eins],[]}}
3> B2 = erlang_ringbuffer:add(zwei, B1).
{ringbuffer,3,2,{[zwei],[eins]}}
4> B3 = erlang_ringbuffer:add(drei, B2).
{ringbuffer,3,3,{[drei,zwei],[eins]}}
5> B4 = erlang_ringbuffer:add(vier, B3).
{ringbuffer,3,3,{[vier,drei],[zwei]}}
6> erlang_ringbuffer:getFirst(B4).      
vier
7> erlang_ringbuffer:getAll(B4).  
[zwei,drei,vier]
````
An OTP library

Build
-----

    $ rebar3 compile
