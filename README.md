# README

This README would normally document whatever steps are necessary to get the
application up and running.

Things you may want to cover:

* Ruby version

* System dependencies

* Configuration

* Database creation

* Database initialization

* How to run the test suite

* Services (job queues, cache servers, search engines, etc.)

* Deployment instructions

* ...

# Checks for Understanding
1. Define CRUD.
* CRUD is an acronym that stands for Create, Read, Update, Destroy. These 4 functions are components of the model in the MVC. The model is responsible for connecting our database with our controller for our app. Let’s say we have an app with a database of users. To access the database, we need to send a request to that database, and that request can take a few different forms.
  * Create - Creates a instance of data in our database
  * Read - Read preexisiting instances of data in our database
  * Update - Update the value(s) of preexisiting instances of data in our database
  * Destroy - Remove data from our database
2. Define MVC.
*  The MVC is a relationship model for web applications. The three components are the Model, the View, and the Controller. Each component has a unique responsibility in the dynamic. The Controller is the hub where actions are routed through. It has access to both the Model and the View. When we want to access data from a database, the Controller sends this operation to be handled by the Model. The Model is responsible for communicating data to and from the Controller and the database. Once the Controller has access to the requested data, it will send it to the View for rendering. The View receives data from the Controller to be rendered in the browser.
3. What two files would you need to create/modify for a Rails application to respond to a GET request to /api/v1/tasks, assuming you have a Task model.
* The 2 files needed for create/update functionality are the `routes.rb` file and the `tasks_controller.rb` file. The `routes` file handled URI routing. If the user put a specified location in the browser's URL, we use the `routes` file to point us to where it should take the user. In the `routes` file we specify the following command.
* Route definition in `routes.rb`
```
<HTTP verb> "<URL location>", to: "<URL location>#<Desired method>"
```
the `Desired method` is a class we as programmers set up in the `tasks_manager` file. This should be related to the HTTP Verb we are invoking in the beginning. In the `task_manager` file, we will have a method definition for the `Desired method` This method will define the actions required to access the database the way we want.
* Method declaration from the `task_manager.rb` file
```
def <Desired method>
        render json: Task.<related ActiveRecord inherited method>
    end
```
4. What are params? Where do they come from?
* Params are a tool for dynamically accessing qualities of data instances in our code. For routing we set up a `show` method that will render a data instance in isolation if we include the `:id` of that data instance in our search string.
```
    def show
        render json: Task.find(params[:id])
    end
```
* There are more params for an instance of data, but for our example, we are using the instance's `:id` because it is the primary key, and we can reference unique data instances based on their `:id`
5. What is the purpose of a serializer?
* Serialization is used when we want to return a custom response. Instead of the entire data object. When we are passing data to the View for rendering. We might not care about the `created_at` or `updated_at` KVPs. Using serialization, we can remove these from the data object that is being passed to the view. This is done for optimization when handling data in the front end. 
