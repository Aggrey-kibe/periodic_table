
# Periodic Table Database

A freeCodeCamp Relational Database certification project. It fixes and extends a PostgreSQL database of chemical elements, and provides a Bash script that looks up an element and prints information about it.

## Files

- `element.sh`: the Bash script that queries the database.
- `periodic_table.sql`: a dump of the final `periodic_table` database.

## Database structure

- `elements`: `atomic_number` (primary key), `symbol` (unique, not null), `name` (unique, not null)
- `properties`: `atomic_number` (foreign key to `elements`), `atomic_mass`, `melting_point_celsius`, `boiling_point_celsius`, `type_id` (foreign key to `types`)
- `types`: `type_id` (primary key), `type` (metal, nonmetal, or metalloid)

## Usage

Run the script with an atomic number, a symbol, or a name:

```bash
./element.sh 1
./element.sh H
./element.sh Hydrogen
```

Output:

```
The element with atomic number 1 is Hydrogen (H). It's a nonmetal, with a mass of 1.008 amu. Hydrogen has a melting point of -259.1 celsius and a boiling point of -252.9 celsius.
```

Other behavior:

- No argument prints `Please provide an element as an argument.`
- An element that is not in the database prints `I could not find that element in the database.`

## Restoring the database

```bash
psql -U postgres < periodic_table.sql
```

## Requirements

- PostgreSQL, with a `freecodecamp` user
- Bash
