# Heroku Terminal Commands


1. Add PUBLIC SSH Key to Heroku :
    `$heroku keys:add`


2. Provide a unique name (For ur application):
    `$heroku create <unique-name>`


3. Deploy the changes :
    `$git push heroku master`



# Deploy Flask app to Heroku

1. Longin to *Heroku*
   `$heroku login`

2. Provide a unique name (For ur application):
    `$heroku create <unique-name>` 

3. Check addons
    `$heroku addons`

4. Add addons
   `$ heroku addons:create heroku-postgresql:<plan-name> --app <heroku-app-name>`

	Note- 

	Heroku has two basic plans-
	1. *hobby-dev*
	2. *hobby-basic*

	Heroku-app-name = the unique name that we created for the app

5. Handling config vars if any- 
	
   * List all config vars: `$ heroku config`
   * Get specific config var: `$ heroku config:get GITHUB_USERNAME`

   * Set congig var: `$ heroku config:set GITHUB_USERNAME=joesmith`

   * Remove a config var: `$ heroku config:unset GITHUB_USERNAME=joesmith`

6. Handling Procfile-
   * Create Procfile in project's root directory w/o extension-
	   `$ touch Procfile`
   * Insert into procfile(run.py contains app var.)-
		`web: gunicorn run:app`

7. Create runtime.txt in project's root directory & specify the used python version-
   * `$ touch runtime.txt`
   * inside the runtime.txt `python-3.6.9`
	
8. Create requirements.txt file-
   * This step must be followed after step 7, if in any case problem occurs, delete 
     this file and again create.
   * `$ pip freeze > requirements.txt`
   * If pkg-resources==0.0.0 exists, then remove it, it may cause build-failure.

9. Finally, go to your heroku app's deploy section, then grab the command to add
   remote and push to master branch.

*It's not done yet*

10. Start the python interpretor to create the database:
   * `$ heroku run python`
   * in python interpretor create db as- 
   >> from sweats import db, create_app
   >> db.create_all(app=create_app())
   >> exit()

11. Finally, type to open website: `$ heroku open`

12. Open DB in the heroku server- `$ heroku pg:psql --app sweats`
    Query: sweats::DATABASE=> SELECT * FROM customers;
