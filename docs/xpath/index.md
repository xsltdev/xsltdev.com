---
hide:
  - navigation
  - toc
---

# XPath Functions

## fn

<style>div.columns > p:first-child {margin-top: 0}</style>
<div class="columns" style="column-width: 10rem;" markdown="1">
[`fn:abs`](fn-abs.md)

[`fn:accumulator-after`](fn-accumulator-after.md)

<!--
accumulator-before

adjust-date-to-timezone

adjust-dateTime-to-timezone

adjust-time-to-timezone

analyze-string

apply

available-environment-variables

available-system-properties

avg

base-uri

boolean

ceiling

codepoint-equal

codepoints-to-string

collation-key

collection

compare

concat

contains

contains-token

copy-of

count

current

current-date

current-dateTime

current-group

current-grouping-key

current-merge-group

current-merge-key

current-output-uri

current-time

data

dateTime

day-from-date

day-from-dateTime

days-from-duration

deep-equal

default-collation

default-language

distinct-values

doc

doc-available

document

document-uri

element-available

element-with-id

empty

encode-for-uri

ends-with

environment-variable

error

escape-html-uri

exactly-one

exists

false

filter

floor

fold-left

fold-right

for-each

for-each-pair

format-date

format-dateTime

format-integer

format-number

format-time

function-arity

function-available

function-lookup

function-name

generate-id

has-children

head

hours-from-dateTime

hours-from-duration

hours-from-time

id

idref

implicit-timezone

in-scope-prefixes

index-of

innermost

insert-before

iri-to-uri

json-doc

json-to-xml

key

lang

last

load-xquery-module

local-name

local-name-from-QName

lower-case

matches

max

min

minutes-from-dateTime

minutes-from-duration

minutes-from-time

month-from-date

month-from-dateTime

months-from-duration

name

namespace-uri

namespace-uri-for-prefix

namespace-uri-from-QName

nilled

node-name

normalize-space

normalize-unicode

not

number

one-or-more

outermost

parse-ietf-date

parse-json

parse-xml

parse-xml-fragment

path

position

prefix-from-QName

put

QName

random-number-generator

regex-group

remove

replace

resolve-QName

resolve-uri

reverse

root

round

round-half-to-even

seconds-from-dateTime

seconds-from-duration

seconds-from-time

serialize

snapshot

sort

starts-with

static-base-uri

stream-available

string

string-join

string-length

string-to-codepoints

subsequence

substring

substring-after

substring-before

sum

system-property

tail

timezone-from-date

timezone-from-dateTime

timezone-from-time

tokenize

trace

transform

translate

true

type-available

unordered

unparsed-entity-public-id

unparsed-entity-uri

unparsed-text

unparsed-text-available

unparsed-text-lines

upper-case

uri-collection

xml-to-json

year-from-date

year-from-dateTime

years-from-duration

zero-or-one

</div>

## math

<div class="columns" style="column-width: 10rem;" markdown="1">

acos

asin

atan

atan2

cos

exp

exp10

log

log10

pi

pow

sin

sqrt

tan

</div>

## map

<div class="columns" style="column-width: 10rem;" markdown="1">

contains

entry

find

for-each

get

keys

merge

put

remove

size

</div>

## array

<div class="columns" style="column-width: 10rem;" markdown="1">

append

filter

flatten

fold-left

fold-right

for-each

for-each-pair

get

head

insert-before

join

put

remove

reverse

size

sort

subarray

tail

</div>

## saxon

<div class="columns" style="column-width: 10rem;" markdown="1">

adjust-to-civil-time

analyze-uri

array-member

base64Binary-to-octets

base64Binary-to-string

characters

column-number

compile-query

compile-stylesheet

current-mode-name

decimal-divide

deep-equal

discard-document

doc

EQName

escape-NCName

eval

evaluate

evaluate-node

expression

function-annotations

get-pseudo-attribute

group-starting

has-same-nodes

hexBinary-to-octets

hexBinary-to-string

highest

in-scope-namespaces

in-summer-time

index

index-where

is-defaulted

is-NaN

is-whole-number

items-after

items-before

items-from

items-until

key-map

last-modified

leading

line-number

lowest

map-search

message-count

namespace-node

new-attribute

new-comment

new-document

new-element

new-processing-instruction

new-text

object-map

octets-to-base64Binary

octets-to-hexBinary

parse

parse-dateTime

parse-html

path

pedigree

print-stack

query

read-binary-resource

replace-with

schema

send-mail

serialize

slice

stream

string-to-base64Binary

string-to-hexBinary

string-to-utf8

system-id

timestamp

transform

tunnel-params

type

type-annotation

unescape-NCName

unindexed

unparsed-entities

validate

with-pedigree

xquery
-->

</div>

## exslt

<!-- div class="columns" style="column-width: 10rem;" markdown="1">

node-set

object-type

</div -->

## date

<!-- div class="columns" style="column-width: 10rem;" markdown="1">

add

add-duration

date

date-time

day-abbreviation

day-in-month

day-in-week

day-in-year

day-name

day-of-week-in-month

difference

duration

hour-in-day

leap-year

minute-in-hour

month-abbreviation

month-in-year

month-name

second-in-minute

seconds

sum

time

week-in-month

week-in-year

year

</div -->

## exslt-math

<!-- div class="columns" style="column-width: 10rem;" markdown="1">

abs

acos

asin

atan

atan2

constant

cos

exp

highest

log

lowest

max

min

power

random

sin

sqrt

tan

</div -->

## random

random-sequence

## set

<!-- div class="columns" style="column-width: 10rem;" markdown="1">

difference

distinct

has-same-node

intersection

leading

trailing

</div -->

## arch

<!-- div class="columns" style="column-width: 10rem;" markdown="1">

create

create-map

delete

delete-map

entries

entries-map

entry-names

extract-binary

extract-binary-map

extract-map

extract-text

extract-text-map

options

options-map

update

update-map

</div -->

## bin

<!-- div class="columns" style="column-width: 10rem;" markdown="1">

and

bin

decode-string

encode-string

find

from-octets

hex

insert-before

join

length

not

octal

or

pack-double

pack-float

pack-integer

pad-left

pad-right

part

shift

to-octets

unpack-double

unpack-float

unpack-integer

unpack-unsigned-integer

xor

</div -->

## file

<!-- div class="columns" style="column-width: 10rem;" markdown="1">

append

append-binary

append-text

append-text-lines

base-dir

children

copy

create-dir

create-temp-dir

create-temp-file

current-dir

delete

dir-separator

exists

is-dir

is-file

last-modified

line-separator

list

move

name

parent

path-separator

path-to-native

path-to-uri

read-binary

read-text

read-text-lines

resolve-path

size

temp-dir

write

write-binary

write-text

write-text-lines

</div -->

## sql

<!-- div class="columns" style="column-width: 10rem;" markdown="1">

connect

delete

execute

insert

prepared-query

prepared-statement

query

update

</div -->
