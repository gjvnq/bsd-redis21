# Database

## Main Graph

Key name: `graph`

Node types:

  * Person
  * Group
  * Slot
  * Question

Relationships:

  * Answers
  * MemberOf
  * Offers
  * Compatibility Value

## Nodes

### Person

Represents a natural person.

Label: `Person`

Properties:

| Name       | Type   | Description |
| ---------- | ------ | ----------- |
| `uuid`     | string | Person's UUID. |
| `email`    | string | Person's email. |
| `password` | string | Person's password hash. |
| `name`     | string | Person's abbreviated name (up to 40 characters). |
| `desc`     | string | Short description of the person. |

### Group

Represents a group of natural persons.

Label: `Group`

Properties:

| Name       | Type   | Description |
| ---------- | ------ | ----------- |
| `uuid`     | string | Group's UUID. |
| `name`     | string | Group's abbreviated name (up to 40 characters). |
| `desc`     | string | Short description of the group. |

### Slot

Represents an "offer" or "search" for a natural person or group.
Rough translation of the Portuguese word *vaga* meaning free slot or position, vacancy, parking space.

Label: `Slot`

Properties:

| Name       | Type   | Description |
| ---------- | ------ | ----------- |
| `uuid`     | string | Slot UUID. |
| `title`    | string | Title of the seat. (e.g. "Web dev", "Logistics folk") |
| `desc`     | string | Short description of the seat. |

### Question

Represents a multiple choice question.

Label: `Question`

Properties:

| Name              | Type    | Description                               |
| ----------------- | ------- | ----------------------------------------- |
| `uuid`            | string  | Question's UUID.                          |
| `title`           | string  | The question enunciation.                 |
| `help`            | string  | Text to further explain the question.     |
| `minsel`          | integer | Minimum answers a respondent must choose. |
| `maxsel`          | integer | Maximum answers a respondent must choose. |
| `options`         | array   | Answers available for choice.             |
| `options[].id`    | integer | The option id (used for comparison).      |
| `options[].text`  | string  | The answer option text.                   |

## Relationships

### Answers

Label: `ANSWERS`

From: `Peron`, `Group`, `Slot`

To: `Question`

Properties:

| Name          | Type             | Description                                    |
| ------------- | ---------------- | ---------------------------------------------- |
| `answers`     | array of integer | Answers given to the question.                 |
| `accepts`     | array of integer | Answers accepted to the question.              |
| `importance`  | integer          | Value from 0 to 100 giving                     |
| `comment`     | string           | Optional comments explaining the choices made. |
| `last_change` | integer          | Timestamp of the last time this was changed.   |

### Member Of

Label: `MEMBER_OF`

From: `Peron`

To: `Group`

Properties:

| Name   | Type   | Description                                                  |
| ------ |------- | ------------------------------------------------------------ |
| `role` | string | Optional string explaing the person's role within the group. |

### Offers

Label: `OFFERS`

From: `Peron`, `Group`

To: `Slot`

Properties: none.

### Compatibility Value

Label: `COMPATIBILITY_VALUE`

From: `Peron`, `Group`

To: `Slot`

Properties:

| Name              | Type    | Description                                    |
| ----------------- |-------- | ---------------------------------------------- |
| `grade_to_slot`   | number  | Compatibility of the person/group to the slot. |
| `grade_from_slot` | number  | Compatibility of the slot to the person/group. |
| `grade_final`     | number  | Geometric average of the two previous values.  |
| `last_change`     | integer | Timestamp of the last time this was changed.   |