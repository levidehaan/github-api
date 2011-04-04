Github API Js
===============
This file has been modified and only works in environments that allow crossdomain scripting such as the BlackBerry Playbook with the WebWorks SDK.
You must also use jQuery to use this library.

Exposes `gh` to the global environment. Tries to follow both the form of GithubHTTP API and JS style. 

You cannot load javascript files in using this library yet, as it gets the data from github inside `<script>` tags.

so really the gists wont work unless you know for sure you wont get any with JS in them, same with looking at repo code that has JS in it.

###Example Code

>##Authentication
>    authenticating as yourself, I'd recommend using something like Amplify to store the user credentials in localstorage
>
>        amplify.store("username", "YourUserName");
>        amplify.store("token", "yourincrediblylongandtotallyawesometoken");
>        gh.authenticate(amplify.store("username"), amplify.store("password"));
>        var user = gh.user(amplify.store("username"));`
    
>##User Information
>  this pulls data showing your user information from github puts your gravatar image inside a div
>
>       user.show(function (data) {
>            var data = data.user
>            console.log(data);
>            $('#somediv").html('<img src="http://gravatar.com/avatar/' + data.gravatar+id + '.jpg?s=80">');
>        });

>##Repository Information
>    show a users repositories, iterates through them and then appends them to a div
>
>        new repo.constructor.forUser(amplify.store("username"), RepoListCallback, data);`
>    
>        function RepoListCallback(data){
>            console.log(data);
>             if(data.repositories.length > 0) {
>                   for(var r=0;r<data.repositories.length; r++){
>                       $('<h1>' + data.repositories[r].name + '</h1>').appendTo('#somediv');
>                   }
>              }
   

>##Sending data
>    grabbing data from a form and sending it to update a user
>
>        var params = {
>                "company" : $("#companyname").val(),
>                "name"      : $("#name").val
>         }
>
>         gh.user(user).update(params);
>
>   There is no callback available for sending data

   
###COMPLETE
========

* Authentication
* Users
* Repos
* Commits
* Issues
* Gists
* Network
* Objects

###TODO
====
* Make calls to github to pull repository files without using `<script>`
* Documentation
