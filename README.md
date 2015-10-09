###Same same, but different###

by Lars Nedberg

Original: https://github.com/henloen/sommer-2014, owners Lars Nedberg and Henrik Loennechen.
Project was then forked and modified: https://github.com/arhplanet/sommer-2014, owner Arne-Richard Hofsøy (arhplanet@gmail.com
This version is a fork of the work made by Arne-Richard Hofsøy. Owner of this version: Lars Nedberg (lars.nedberg@gmail.com).


The application mainly consists of two subparts.
Part 1 is a questionnaire where the user answers an image-questionnaire-form.
Answers obtained are saved in a database, and can be viewed in the admin part of the application.
Both the user and the admin part of the application can be accessed from the main menu (the first screen when accessing the application)

Part 2 is presenting statistics from the answers gathered in part 1.

####Installation and running#####
1. Clone this repo.
     ```bash
     git clone https://github.com/bouvet/same-same.git
     ```

2. Download and install node.js, either using your system package manager or from [nodejs.org](https://nodejs.org)
(version 0.12.7 was used during development and version 0.10 has been tested).

3. Download and install MySQL and run the scripts in the `sql` subfolder using the following commands
where *dbuser* is a MySQL user.
with the necessary privileges to create new databases (e.g. the MySQL *root* user). The database can be installed on
a separate host if desired in which case the two SQL scripts would need to be transferred to that host.
     ```bash
     mysql -u dbuser -p < ss_answers.sql
     mysql -u dbuser -p < ss_participants.sql
     ```
     I could also be useful to seed the database with answers provided by Bouvet employees. This can be achieved by
     running the SQL file called `samesame_etter_bouvet.sql` located in the project root folder.
     ```bash
     mysql -u dbuser -p samesame < samesame_etter_bouvet.sql
     ```
     *NOTE:* If using Windows the *mysql* command is most likely not on the path, in which case you will need to type the
     full path to the command (defaults to: `"C:\Program Files\MySQL\MySQL Server 5.x\bin\mysql"`).

4. Create a file named `config.local.js` in the `app` subfolder and make sure it contains the following, replacing
the values with the ones specific to your installation (e.g. `dburl: 'localhost'` if the database server is on the same host).
     ```javascript
     'use strict';
     var dbOptions = {
          dburl: 'yourDBurl',
          dbuser: 'yourDBuser',
          dbpassword: 'yourDBpassword'
     }
     exports.dbOptions = dbOptions;
     ```

5. Run *npm start* from the root level of the project. This should install all further dependencies and fire up the application.

6. Access the application at **ipaddress:port** (e.g. localhost:3000).

####Usage####
#####Recommended equipment#####
1. A computer to run the server.
2. One or more tablets for users to answer the questionnaire.
3. One or more large screens to display the statistics slideshows.
4. A router to provide a local network for the computer and tablets.
