sumo_db

# About
This is a work in progress. There's also [an article](http://marcelog.github.com/articles/erlang_persistence_entities.html) about sumo_db.

**sumo_db** aims to ease db access for erlang applications. It offers a very
simple persistance layer capable of interacting with different db's, while
offering a consistent api to your code.

# Overview
 * sumo_db gives you a standard way to define your db schema, no matter the
 db implementation (mongo, mysql, redis, or sqlite3).
 * Your entities encapsulate behavior in code (functions in module) and state
 into proplists.
 * sumo is the main module. It translates to and from #sumo_doc records into your
 own state.
 * Each repo is a process *sumo_repo* that calls the actual db driver
 (e.g: sumo_repo_mysql).
 * Some native domain events are supported, that are dispatched through
 a gen_event:notify/2 automatically when an entity is created, updated, deleted.
 Also when a schema is created and when all entities of a given type are
 deleted. Events are described in [this article](http://marcelog.github.com/articles/erlang_epers_persist_entities_domain_events.html)

# About dependencies
In order to avoid having sumo_db require the db drivers (like emysql, emongo, etc),
**you** should include them in your application. Currently, sumo_db has been tested
with the following drivers and versions.

# DB's supported
 * mysql (uses [emysql](https://github.com/Eonblast/Emysql))
 * mongodb (uses [emongo](https://github.com/JacobVorreuter/emongo))

# In progress
 * redis (uses [eredis](https://github.com/wooga/eredis))
 * sqlite3 (uses [erlang-sqlite3](https://github.com/alexeyr/erlang-sqlite3))

# Planned
  * mnesia
  * memory

# Example
See: [**examples/blog**](https://github.com/inaka/sumo_db/tree/master/examples/blog)
for a full example. To run it, while being in the top level directory:

    make all blog

# TODO
 * Get rid of atoms and use lists.
