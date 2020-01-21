# Table of Contents

- [Table of Contents](#table-of-contents)
  - [Installing dependencies](#installing-dependencies)
  - [Bootstraping Python application](#bootstraping-python-application)
    - [Managing Entities with SQLAlchemy ORM](#managing-entities-with-sqlalchemy-orm)
    - [Managing HTTP Requests with Flask](#managing-http-requests-with-flask)
    - [Handling CORS on Flask Apps](#handling-cors-on-flask-apps)
  - [Bootstrapping the Angular Application](#bootstrapping-the-angular-application)
    - [Consuming Flask Endpoints with Angular](#consuming-flask-endpoints-with-angular)
  - [Citations](#citations)
  

## Installing dependencies

Follow below steps to get started on this full stack how-to notes for develop using Python, Flask, and Angular to build a web application based on a modern architecture.
  

1. **pipenv** tool - Install pipenv using following in terminal
   ``` 
   pip install pipenv 
   ```
2. [Install Docker](https://docs.docker.com/install/) and run below docker run command to create database in local.
   <pre>
   docker run --name online-exam-db \
    -p 5432:5432 \
    -e POSTGRES_DB=online-exam \
    -e POSTGRES_PASSWORD=0NLIN3-ex4m \
    -d postgres
    </pre>
3. Install **node** and **npm** from [nodejs](https://nodejs.org/en/download/)
4. Install angular cli using below command from terminal
   ```
   npm install -g @angular/cli
   ```

***
[Top](#table-of-contents)
***

## Bootstraping Python application

1. Create a directory to hold all the frontend and the backend source code of your app, and initialize git repository.
   
   ```
   #create the project root directory
   mkdir online-exam

   #move into it
   cd online-exam

   #initialize it as a Git repository 
   git init
   ```
2. Create a directory for backend application.
   
   ```
   #create directory to hold backend source code
   mkdir backend

   #move into it
   cd backend
   ```
3. Create virtual environment using **pipenv**
   
   ```
   #initialize the virtual environment
   pipenv --three
   ```
4. Create .gitignore file in the project root directory and copy the rules from this [URL](https://raw.githubusercontent.com/auth0-blog/online-exam/master/.gitignore)

***
[Top](#table-of-contents)
***

### Managing Entities with SQLAlchemy ORM

1. Define entities and to configure SQLAlchemy to persist and retrieve instances of these entities.
2. Use **pipenv** to install the sqlalchemy package and a driver to connect to your database.
3. If you are using PostgreSQL, you can use the ```psycopg2-binary``` driver alongside with SQLAlchemy.
4. Check this [page](https://docs.sqlalchemy.org/en/13/core/engines.html#supported-databases) to choose a good driver.
5. Use below command to install ```sqlalchemy``` and ```psycog2-binary```.

    ```
    #install sqlalchemy and psycopg2 on the venv
    pipenv install sqlalchemy psycopg2-binary
    ```
6. Create entities as below. The last touch command creates the file that will hold a class called Entity. You will use this class as the superclass to all your entities. This will be useful to avoid having to repeat some boilerplate code to connect to the database and to define some common properties (e.g. id and created_at)
   
   ```
   #create directories
   mkdir -p src/entities

   #create file to mark src as a module
   touch src/__init__.py

   #create file to mark entities as a module
   touch src/entities/__init__.py

   #create file to hold some boilerplate code
   touch src/entities/entity.py
   ```

7. Use boiler plate code in entity.py to connect to the database and to define some common properties (e.g. id and created_at)

    ```
    #coding=utf-8

    from datetime import datetime
    from sqlalchemy import create_engine, Column, String, Integer, DateTime
    from sqlalchemy.ext.declarative import declarative_base
    from sqlalchemy.orm import sessionmaker

    db_url = 'localhost:5432'
    db_name = 'online-exam'
    db_user = 'postgres'
    db_password = '0NLIN3-ex4m'
    engine = create_engine(f'postgresql://{db_user}:{db_password}@{db_url}/{db_name}')
    Session = sessionmaker(bind=engine)

    Base = declarative_base()


    class Entity():
    id = Column(Integer, primary_key=True)
    created_at = Column(DateTime)
    updated_at = Column(DateTime)
    last_updated_by = Column(String)

    def __init__(self, created_by):
        self.created_at = datetime.now()
        self.updated_at = datetime.now()
        self.last_updated_by = created_by
    ```

8. Create exam.py to represent first entity.
   
   ```
   touch src/entities/exam.py
   ```

9. Insert following code.
   
   ```
    #coding=utf-8

    from sqlalchemy import Column, String

    from .entity import Entity, Base


    class Exam(Entity, Base):
        __tablename__ = 'exams'

        title = Column(String)
        description = Column(String)

        def __init__(self, title, description, created_by):
            Entity.__init__(self, created_by)
            self.title = title
            self.description = description
   ```

   Here, you are defining a class called Exam that inherits from Entity and from Base. This entity contains, besides the properties defined by its superclasses, two properties: title and description. Besides that, this class also defines that instances of it must be persisted to and retrieved from a table called exams.


10.  Create a script called main.py in the src directory to test if they are really connecting to the database.

    ```
    touch src/main.py
    ```

    ```
    #coding=utf-8

    from .entities.entity import Session, engine, Base
    from .entities.exam import Exam

    #generate database schema
    Base.metadata.create_all(engine)

    #start session
    session = Session()

    #check for existing data
    exams = session.query(Exam).all()

    if len(exams) == 0:
        #create and persist dummy exam
        python_exam = Exam("SQLAlchemy Exam", "Test your knowledge about SQLAlchemy.", "script")
        session.add(python_exam)
        session.commit()
        session.close()

    #reload exams
    exams = session.query(Exam).all()

    #show existing exams
    print('###Exams:')
    for exam in exams:
        print(f'({exam.id}) {exam.title} - {exam.description}')
    ```
   
* It starts by importing Session, engine, and Base from the .entities.entity module.
* Then, it imports the Exam class from the .entities.exam module.
* Then, it generates (if needed) the database schema.
* After generating the schema, it queries all instances of Exam.
* Then, if there are no exams on the database, it creates a new one and queries all instances of the Exam class again.
* Lastly, it prints the exams retrieved from the database.

11. To run this script main.py, you will have to activate the virtual environment (created by pipenv) then use python to trigger the src.main module.

```
#activate virtual environment
pipenv shell

#run main module
python -m src.main
```

12. If everything works as expected, your module will create an instance of Exam, persist to the database, and print its details on the terminal.
    
```
(base) Karthiks-MacBook-Air:backend karthikkappagantula$ ls -l
total 16
-rw-r--r--  1 karthikkappagantula  staff   177 Jan 19 08:49 Pipfile
-rw-r--r--  1 karthikkappagantula  staff  3827 Jan 19 08:49 Pipfile.lock
drwxr-xr-x  5 karthikkappagantula  staff   160 Jan 19 14:11 src
(base) Karthiks-MacBook-Air:backend karthikkappagantula$ pipenv shell
Launching subshell in virtual environment…

The default interactive shell is now zsh.
To update your account to use zsh, please run `chsh -s /bin/zsh`.
For more details, please visit https://support.apple.com/kb/HT208050.
bash-3.2$  . /Users/karthikkappagantula/.local/share/virtualenvs/backend-zD0mafRO/bin/activate
(backend) bash-3.2$ python -m src.main
###Exams:
(1) SQLAlchemy Exam - Test your knowledge about SQLAlchemy.
(backend) bash-3.2$ 
```

***
[Top](#table-of-contents)
***

### Managing HTTP Requests with Flask

1. Now that your app is connected to a database, it's time to transform it into a Flask web application. To do so, the first thing you will need is to install **flask** and **marshamallow**

```
pipenv install flask marshmallow
```

2. Update exam.py as follows:
   
<pre>
#coding=utf-8

from marshmallow import Schema, fields

#... other import statements ...

#... Exam class definition ...

class ExamSchema(Schema):
    id = fields.Number()
    title = fields.Str()
    description = fields.Str()
    created_at = fields.DateTime()
    updated_at = fields.DateTime()
    last_updated_by = fields.Str()
</pre>

In the new version of this file, you are using the Schema class of marshmallow to define a new class called ExamSchema. You will use this class to transform instances of Exam into JSON objects.

3. After defining ExamSchema, you can refactor the ./src/main.py file to expose two endpoints.

<pre>
#coding=utf-8

from flask import Flask, jsonify, request

from .entities.entity import Session, engine, Base
from .entities.exam import Exam, ExamSchema

#creating the Flask application
app = Flask(__name__)

#if needed, generate database schema
Base.metadata.create_all(engine)


@app.route('/exams')
def get_exams():
    #fetching from the database
    session = Session()
    exam_objects = session.query(Exam).all()

    #transforming into JSON-serializable objects
    schema = ExamSchema(many=True)
    exams = schema.dump(exam_objects)

    #serializing as JSON
    session.close()
    return jsonify(exams)


@app.route('/exams', methods=['POST'])
def add_exam():
    #mount exam object
    posted_exam = ExamSchema(only=('title', 'description'))\
        .load(request.get_json())

    exam = Exam(**posted_exam, created_by="HTTP post request")

    #persist exam
    session = Session()
    session.add(exam)
    session.commit()

    #return created exam
    new_exam = ExamSchema().dump(exam).data
    session.close()
    return jsonify(new_exam), 201
</pre>   

This file now creates a Flask application, based on SQLAlchemy and PostgreSQL, that is capable of accepting POST requests to create new instances of exam and capable of accepting GET requests to serialize these instances as a JSON array.

4. To facilitate running this application, you can create a script called bootstrap.sh in the backend directory with the following code:
   
<pre>
#!/bin/bash
export FLASK_APP=./src/main.py
source $(pipenv --venv)/bin/activate
flask run -h 0.0.0.0
</pre>

This script does three things:

* it sets ./src/main.py as the value of the FLASK_APP environment variable (this is needed by the last command);
* it activates the virtual environment;
* and it runs flask listening on all interfaces (-h 0.0.0.0).

5. To test everything, use below commands
   
   <pre>
    # make script executable
    chmod u+x bootstrap.sh

    # execute script in the background
    ./bootstrap.sh &

    # create a new exam
    curl -X POST -H 'Content-Type: application/json' -d '{
    "title": "TypeScript Advanced Exam",
    "description": "Tricky questions about TypeScript."
    }' http://0.0.0.0:5000/exams

    # retrieve exams
    curl http://0.0.0.0:5000/exams
   </pre>

Besides using curl, you can also fetch exams by browsing to http://0.0.0.0:5000/exams.

***
[Top](#table-of-contents)
***

### Handling CORS on Flask Apps

1. As your Flask app will receive requests from a SPA, you will need to allow CORS on it. If you don't do so, most browsers will block requests to your API because the backend does not explicitly allow Cross-Origin Resource Sharing (CORS). There is a Flask module called **flask-cors** that is easy to configure. 
   
2. Install **flask-cors** in the **backend** directory
   ```
   pipenv install flask-cors
   ```
3. Update **main.py** to use **flask-cors**

   <pre>
    # coding=utf-8

    from flask_cors import CORS
    #other import statements 

    #creating the Flask application
    app = Flask(__name__)
    CORS(app)

    #create_all(engine) and endpoint definitions
   </pre>

*Check the [official documentation of the flask-cors module](https://flask-cors.readthedocs.io/en/latest/#resource-specific-cors) to learn how to make the application more restrictive for productionized applications.*

4. Commit the changes to git and leave the app running.
   
   <pre>
   #commit your progress
   git add . && git commit -m "enabling CORS"

   #run the Flask app in the background
   ./bootstrap.sh &
   </pre>

***
[Top](#table-of-contents)
***

## Bootstrapping the Angular Application

1. Move back to the project root directory and issue **ng new frontend**
   
    <pre>
    #change working directory to project root
    cd ..

    #run @angular/cli to bootstrap the Angular app. Use defaults for now.
    ng new frontend

    #move working directory to your frontend app
    cd frontend

    #commit template Angular project
    git add . && git commit -m "bootstrapping an Angular project"
    </pre>

***
[Top](#table-of-contents)
***

### Consuming Flask Endpoints with Angular

1. After creating your Angular app, the next thing you will need is to create a file called **env.ts** inside the **./frontend/src/app** directory with the following code:
   
   <pre>
   export const API_URL = 'http://localhost:5000';
   </pre>

This TypeScript module simply exports a single constant (API_URL) that references your Flask backend application running locally. 

2. 
***
[Top](#table-of-contents)
***

## Citations
[Source content](https://auth0.com/blog/using-python-flask-and-angular-to-build-modern-apps-part-1/)<br>
[SQLAlchemy ORM](https://auth0.com/blog/sqlalchemy-orm-tutorial-for-python-developers/)<br>
[Docker install](https://docs.docker.com/install/)<br>
[CORS](https://developer.mozilla.org/en-US/docs/Web/HTTP/CORS)<br>
[Flask-CORS](https://flask-cors.readthedocs.io/en/latest/#resource-specific-cors)<br>