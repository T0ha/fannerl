fannerl
======

fannerl is erlang bindings to to the [Fast Artifical Neural Network,
FANN](http://leenissen.dk/fann). The library is curently under
construction. The intention is to create a basic literal translation
of the C api to erlang and then create a layer on top of fannerl that
handles concurrency and makes the operations threadsafe which fannerl
will not be. FANN itself is not threadsafe. The FANN library code is
called using NIFs which is explained
[here](http://www.erlang.org/doc/man/erl_nif.html).

To be able to run the current code I recommend that you use rebar. You
will also need to have FANN installed on your system. I have only
tested it with FANN 2.1.0. When compiling the fann_nif.c you need to
link to fann or it will fail. This is handled automatically if you're
running rebar.

This has only been tested on linux.

I have isolated a fault when using fann_sigmoid as activation
function. If you set a neuron to use fann_sigmoid and then do
fann_get_activation_function you will crash. Oddly enough it works
with other types of activation functions.