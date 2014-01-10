# Rebar-friendly fork of Rabbit common

This is a fork from jbrisbin/rabbit_common intended to allow jbrisbin/amqp_client to work correctly with reltool.

The following changes were made to the upstream version:

1. Removed gen_server2.erl - It conflicts with the dependency gen_server2
2. Removed priority_queue.erl - Same reason
3. Updated rebar.config to not look for the removed files.
4. Added gen_server2 as an external dependency to allow us to play nicely with other things that depend on it.

This is a fork of the rabbit_common dependency, which is needed by the 
[official RabbitMQ/AMQP Erlang client](https://github.com/rabbitmq/rabbitmq-erlang-client). 

It's meant to be included in your rebar projects in your rebar.config file:

		{deps, [
			{rabbit_common, ".*", {git, "git://github.com/jbrisbin/rabbit_common.git", "rabbitmq-3.0.0"}}
		]}.

The "master" branch of this port is a simple re-packaging of the rabbit_common AMQP client dependency.

The "community" branch, however, is a port of the RabbitMQ source code with additional strict compilation 
checking turned on and the source code edited to eliminate warnings. It should be 100% compatible with the 
unaltered source code. The community branch is simply a tweak to allow projects that depend on rabbit_common 
to not have to deal with the warnings issued by the compiler in the unaltered RabbitMQ code.

To use the "community" branch in your project, which includes stricter compilation settings, add "-community" 
to the version tag:

		{deps, [
			{rabbit_common, ".*", {git, "git://github.com/jbrisbin/rabbit_common.git", "rabbitmq-3.0.0-community"}}
		]}.

### License 

This package, just like the the RabbitMQ server, is licensed under the MPL. For the MPL, please see LICENSE-MPL-RabbitMQ.
