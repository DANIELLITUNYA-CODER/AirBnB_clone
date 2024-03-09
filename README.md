# HBNB - The Console

This repository contains the initial stage of a student project to build a clone of the AirBnB website. This stage implements a backend interface, or console, to manage program data. Console commands allow the user to create, update, and destroy objects, as well as manage file storage. Using a system of JSON serialization/deserialization, storage is persistent between sessions.

## Repository Contents by Project Task

### Tasks

| Task                     | Files                                                      | Description                                                        |
|--------------------------|------------------------------------------------------------|--------------------------------------------------------------------|
| 0: Authors/README File   | `AUTHORS`                                                  | Project authors                                                    |
| 1: Pep8                  | N/A                                                        | All code is pep8 compliant                                         |
| 2: Unit Testing          | `/tests`                                                   | All class-defining modules are unittested                          |
| 3. Make BaseModel        | `/models/base_model.py`                                    | Defines a parent class to be inherited by all model classes        |
| 4. Update BaseModel w/ kwargs | `/models/base_model.py`                               | Add functionality to recreate an instance of a class from a dictionary representation |
| 5. Create FileStorage class | `/models/engine/file_storage.py`<br>`/models/__init__.py`<br>`/models/base_model.py` | Defines a class to manage persistent file storage system |
| 6. Console 0.0.1         | `console.py`                                               | Add basic functionality to console program, allowing it to quit, handle empty lines and ^D |
| 7. Console 0.1           | `console.py`<br>`/models/engine/file_storage.py`<br>`/models/user.py` | Update the console with methods allowing the user to create, destroy, show, and update stored data |
| 8. Create User class     | `console.py`<br>`/models/engine/file_storage.py`<br>`/models/user.py` | Dynamically implements a user class                                |
| 9. More Classes          | `/models/user.py`<br>`/models/place.py`<br>`/models/city.py`<br>`/models/amenity.py`<br>`/models/state.py`<br>`/models/review.py` | Dynamically implements more classes                                |
| 10. Console 1.0          | `console.py`<br>`/models/engine/file_storage.py`           | Update the console and file storage system to work dynamically with all classes update file storage |

## General Use

First clone this repository.

Once the repository is cloned locate the "console.py" file and run it as follows:

/AirBnB_clone$ ./console.py
When this command is run the following prompt should appear:

This prompt designates you are in the "HBnB" console. There are a variety of commands available within the console program.

## Commands

* `create` - Creates an instance based on given class
* `destroy` - Destroys an object based on class and UUID
* `show` - Shows an object based on class and UUID
* `all` - Shows all objects the program has access to, or all objects of a given class
* `update` - Updates existing attributes an object based on class name and UUID
* `quit` - Exits the program (EOF will as well)

## Alternative Syntax

Users are able to issue a number of console command using an alternative syntax:

Usage: `<class_name>.<command>([<id>[name_arg value_arg]|[kwargs]])`

Advanced syntax is implemented for the following commands:

* `all` - Shows all objects the program has access to, or all objects of a given class
* `count` - Return number of object instances by class
* `show` - Shows an object based on class and UUID
* `destroy` - Destroys an object based on class and UUID
* `update` - Updates existing attributes an object based on class name and UUID

## Examples

### Primary Command Syntax

#### Example 0: Create an object

Usage: create <class_name>

(hbnb) create User
(hbnb) create User
12345678-abcd-efgh-ijkl-9876543210ab
(hbnb)
Usage: show <class_name> <_id>

(hbnb) show User 12345678-abcd-efgh-ijkl-9876543210ab
[User] (12345678-abcd-efgh-ijkl-9876543210ab) {'id': '12345678-abcd-efgh-ijkl-9876543210ab', 'created_at': '2024-03-09T12:00:00', 'updated_at': '2024-03-09T12:00:00'}
(hbnb)
Usage: destroy <class_name> <_id>

(hbnb) destroy User 12345678-abcd-efgh-ijkl-9876543210ab
(hbnb) show User 12345678-abcd-efgh-ijkl-9876543210ab
** no instance found **
(hbnb)
Usage: update <class_name> <_id>

(hbnb) update User 12345678-abcd-efgh-ijkl-9876543210ab name "John"
(hbnb) show User 12345678-abcd-efgh-ijkl-9876543210ab
[User] (12345678-abcd-efgh-ijkl-9876543210ab) {'id': '12345678-abcd-efgh-ijkl-9876543210ab', 'created_at': '2024-03-09T12:00:00', 'updated_at': '2024-03-09T12:01:00', 'name': 'John'}
(hbnb)Usage: <class_name>.all()

(hbnb) User.all()
["[User] (12345678-abcd-efgh-ijkl-9876543210ab) {'id': '12345678-abcd-efgh-ijkl-9876543210ab', 'created_at': '2024-03-09T12:00:00', 'updated_at': '2024-03-09T12:01:00', 'name': 'John'}"]
#### Example 1: Destroy a User

Usage: <class_name>.destroy(<_id>)

(hbnb) User.destroy("12345678-abcd-efgh-ijkl-9876543210ab")
(hbnb)
(hbnb) User.all()
(hbnb) []
#### Example 2: Update User (by attribute)

Usage: <class_name>.update(<_id>, <attribute_name>, <attribute_value>)

(hbnb) User.update("12345678-abcd-efgh-ijkl-9876543210ab", age 30)
(hbnb)
(hbnb) User.all()
(hbnb)
