# SmartSeeder for Laravel

Seeding as it is currently done in Laravel is intended only for dev builds, but what if you want to seed a production database with different data from what you use in development? What if you want to seed a table you've added to a database that is currently in production with new data?

Features
========

- Allows you to seed databases in different environments with different values.
- Allows you to "version" seeds, the same way that Laravel currently handles migrations. Running php artisan seed will only run seeds that haven't been run already.
- Overrides Laravel's seeding commands. SmartSeeder will fire when you run
    ```
    php artisan db:seed
    ```
     or
    ```
    php artisan migrate:refresh --seed
    ```

- Prompts you if your database is in production already.
- Allows you to run multiple seeding of the same model/table

When you install SmartSeeder, various artisan commands are made available to you, which mostly mimic the migrations.

- seed           Runs all the seeds in the smartSeeds directory that haven't been run yet.
- seed:make      Makes a new seed class in the environment you specify.
- seed:rollback  Rollback doesn't undo seeding (which would be impossible with an auto-incrementing primary key). It just allows you to rerun the last batch of seeds.
- seed:reset     Resets all the seeds
- seed:refresh   Resets and re-runs all seeds
- seed:install    You don't have to use this... it will be run automatically when you call "seed"

Installation
============

- Add 'Jlapp\SmartSeeder\SmartSeederServiceProvider' to your providers array in app/config/app.php
- Run the migration that adds the seeds table to the database by typing the following on the command line.
    ```
    php artisan migrate --package="vendor/package"
    ```
- Run php artisan config:publish jlapp/smart-seeder to push config files to your app folder if you want to override the name of the seeds folder or the name of the table where seeds are stored