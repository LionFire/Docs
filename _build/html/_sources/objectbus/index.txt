ObjectBus
=========

A data access abstraction framework centered around strongly-typed and (optionally) multi-typed objects.

This is a child project of Vos.

OBase Implementations
=====================

* Filesystem
* Vos
* RaptorKV (experimental)
* Future ideas:
  * SQL-based implementations
    * SQLite3
    * Postgres
  * NoSQL implementations
    * Redis
    * MongoDB or similar
  * Filesystem inside zip archive

Glossary
========

* Handle - a handle to an object.
* OBase - like database, but for objects. These are plugins for OBus
* OBus - short for ObjectBus
* ObjectBus - A basic CRUD layer for objects
* Reference - A URI for a particular object. Used by OBus.
* Vos - Virtual Object System (like a filesystem for objects.)