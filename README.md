# PG'OCaml is a set of OCaml bindings for the PostgreSQL database.

Please note that this is not the first or only PGSQL bindings for
OCaml. Here are the others which you may want to consider:

* [postgresql-ocaml](http://www.ocaml.info/home/ocaml_sources.html)
PostgreSQL-OCaml by Markus Mottl

* [ocamlodbc](http://home.gna.org/ocamlodbc/)
ODBC bindings by Max Guesdon which can be used to access PostgreSQL

* [ocamldbi](http://download.savannah.nongnu.org/releases/modcaml/) a Perl-like
DBI layer by the present author

PG'OCAML is different than the above bindings:

* It ISN'T just a wrapper around the C libpq library.  Instead it's a pure
OCaml library which talks the frontend/backend protocol directly with the
database.

* It has a camlp4 layer which lets you write SQL statements directly in your
code, TYPE SAFE at compile time, with TYPE INFERENCE into the SQL, and using
the full PostgreSQL SQL grammar (sub-selects, PG-specific SQL, etc.).  But
the flip side of this is that you need to have access to the database at
_compile_ time, so the type checking magic can be done; also if you change
the database schema, you will need to recompile your code to check it is
still correctly typed.

* (A minor point) - It requires PostgreSQL >= 7.4. The default interface
(`PGOCaml`) provided is synchronous. But it also supports any asynchronous
interface that implements the `PGOCaml_generic.THREAD` signature.

* It doesn't work with other databases, nor will it ever work with other
databases.

----------------------------------------------------------------------

PG'OCaml (C) Copyright 2005-2009 Merjis Ltd, Richard W.M. Jones (rich@annexia.org)
and other authors (see CONTRIBUTORS.txt for details).

This software is distributed under the GNU LGPL with OCaml linking
exception.  Please see the file COPYING.LIB for full license.

----------------------------------------------------------------------

For an example, please see [tests](https://github.com/darioteixeira/pgocaml/blob/master/tests/test_pgocaml_highlevel.ml)
