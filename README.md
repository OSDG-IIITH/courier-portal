# IIIT Courier Portal

- Pydantic-based models
- Fast

## Installation

```
cp -rv env.example .env  # populate with your own values
docker-compose up -d
```

(_Note: read up on resources mentioned on Slack for debugging help_)

## Routes

### Static files

The `nginx` service serves both static files from the front and backend.

Add staticfiles for
- frontend: to the `rollup` build process OR to
`frontend/dist/`
- backend: to `backend/static`

### API

The `backend` service is to be accessed from the frontend using `/api` prefix.

Thus any backend routes are now `/api/route-to-be-accessed`. Because of this,
the API docs are hosted at `/api/docs`.

### DB Interface

For easy debugging purposes, there is an express mongodb interface provided at
`/db_interface/`. This will probably be obselete since the actual courier portal
database is probably going to be mySQL, but has been included for now for easy
testing

## Schema

### Tables

1. `Courier_Info`
2. `Student`
3. `account`
4. `courier`
5. `information`
6. `pt`

### Definitions

- **[1] Courier Info**

|     Field      |    Type     | Null  |  Key  | Default |      Extra       |
| :------------: | :---------: | :---: | :---: | :-----: | :--------------: |
|  `courier_id`  |   int(11)   |  NO   |  PRI  |  NULL   | `auto_increment` |
| `courier_type` | varchar(30) |  YES  |       |  NULL   |
| `student_name` | varchar(30) |  NO   |       |  NULL   |
|     `date`     |    date     |  NO   |       |  NULL   |
|  `sender_add`  | varchar(40) |  NO   |       |  NULL   |
|    `taken`     |   int(11)   |  NO   |       |  NULL   |
|     `room`     | varchar(20) |  NO   |       |  NULL   |
|  `overlapped`  |   int(11)   |  YES  |       |  NULL   |
|   `matched`    | varchar(20) |  NO   |       |  NULL   |

- **[2] Student**

|    Field     |    Type     | Null  |  Key  | Default | Extra |
| :----------: | :---------: | :---: | :---: | :-----: | :---: |
|  `roll_no`   | varchar(20) |  NO   |  PRI  |  NULL   |
|    `name`    | varchar(40) |  NO   |       |  NULL   |
|  `username`  | varchar(60) |  YES  |       |  NULL   |
|  `room_no`   | varchar(30) |  NO   |       |  NULL   |
|   `phone`    | varchar(12) |  NO   |       |  NULL   |
| `otheremail` | varchar(60) |  NO   |       |  NULL   |


- **[3] Account**

|  Field   |    Type     | Null  |  Key  | Default | Extra |
| :------: | :---------: | :---: | :---: | :-----: | :---: |
|  `name`  | varchar(30) |  YES  |       |  NULL   |       |
| `roomno` | varchar(10) |  YES  |       |  NULL   |       |
| `hostel` | varchar(10) |  YES  |       |  NULL   |       |
| `rollno` | varchar(20) |  YES  |       |  NULL   |       |
| `email`  | varchar(50) |  YES  |       |  NULL   |       |
| `passwd` | varchar(50) |  YES  |       |  NULL   |       |

- **[4] Courier**

|    Field     |     Type     | Null  |  Key  | Default | Extra |
| :----------: | :----------: | :---: | :---: | :-----: | :---: |
| `courierid`  |   int(11)    |  YES  |       |  NULL   |       |
|    `name`    | varchar(30)  |  YES  |       |  NULL   |       |
|   `roomno`   | varchar(10)  |  YES  |       |  NULL   |       |
|   `hostel`   | varchar(10)  |  YES  |       |  NULL   |       |
|    `type`    | varchar(20)  |  YES  |       |  NULL   |       |
|  `fromaddr`  | varchar(100) |  YES  |       |  NULL   |       |
| `date_arrvd` |     date     |  YES  |       |  NULL   |       |
|   `recvd`    |  varchar(5)  |  YES  |       |  'no'   |       |
|  `receiver`  | varchar(30)  |  YES  |       | 'none'  |       |

- **[5] Information**

|   Field    |    Type     | Null  |  Key  | Default | Extra |
| :--------: | :---------: | :---: | :---: | :-----: | :---: |
| `username` | varchar(40) |  NO   |  PRI  |  NULL   |       |
| `password` | varchar(20) |  NO   |       |  NULL   |       |

- **[6] Pt**

|     Field      |  Type   | Null  |  Key  | Default | Extra |
| :------------: | :-----: | :---: | :---: | :-----: | :---: |
|    `rollno`    | int(11) |  NO   |  PRI  |  NULL   |       |
|     `date`     |  date   |  NO   |  PRI  |  NULL   |       |
| `date_entered` |  date   |  NO   |       |  NULL   |       |

