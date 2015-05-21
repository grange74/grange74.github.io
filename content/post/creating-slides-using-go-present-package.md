+++
date = "2015-05-21T23:15:44+11:00"
title = "Creating Slides using Go's present package"

+++

Sick of using Powerpoint? Just want to create simple, clean slides for your next tech presentation?
Well then give Go's present package a try.

## Creating the Slides

Just create a *.slide* file in your favourite text editor. The syntax is pretty simple. The full syntax is documented on the [present package](https://godoc.org/golang.org/x/tools/present) page.

Here is a simple example:

```
Data Center Automation Presentation

* Agenda
- Terraform Example
- Chef Example

* Terraform Example
.image images/terraform-example.png _ 800

* Chef Example
.code code/recipes/default.rb

.code code/attributes/default.rb
```

It should be pretty self-explanatory but just in case:

* The first line is just the title of the Presentation.
* Asterix (*) indicate the title of each slide. 
* Dash (-) indicate a bullet point.
* .image to insert an image using a local relative path.
* .code pulls in code using a local relative path.

## Viewing the Slides

Now to see your slides. You'll need Go installed and setup. Hopefully you already have that otherwise it's about time you [got started :-)](https://golang.org/doc/install).

Pull down the present package:

``` 
go get golang.org/x/tools/cmd/present 
```

That should of created the present binary in your $GOPATH/bin. Now run that from the directory where your slide is.

```
$GOPATH/bin/present
```

If it worked you should see the following: 

```
2015/05/21 23:41:37 Open your web browser and visit http://127.0.0.1:3999
```

Now open your browser and see your slides: [http://localhost:3999/](http://localhost:3999/)



## Tips

1. If you want to share your slides with someone else in the office, you can always change the IP and/or Port that the present binary is binding on:
```
$GOPATH/bin/present -http="192.168.0.103:3999"
```

2.  Add the bin directory to your path so you can just ```present``` to start the slides.
```
export PATH="$GOPATH/bin:$PATH"
```