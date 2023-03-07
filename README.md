# Semantic Web Project: Calendar that follows the Linked Data principles #


# 1. Tools

* Python: RDFLib is a Python library for working with RDF. And we found it simple, yet powerful language for representing information. This library contains
parsers/serializers for almost all of the known RDF serializations. 
* Flask Framework: is written in python. And it is used for easy and fast web application development, and for configuring back-end applications with the front-end
in an easy way, also since our first choose is RDFLib we also choose python framework.
* Postman: is an API platform for building and using APIs. We use postman to accelerate the API Lifecycle - from design, testing, and documentation. 
* ADECal.ics: an ICS file. Which is a calendar file saved in a universal calendar formatused by several programs. 

NOTE: for the necessary installations to run the program please check:
---------------------------------------
# Features

** Generating TURTEL file **
- "TTL_File_Generator.py" file is responsible to generate our RDF graph
* Installation 
  - $ pip install Calendar
  - $ pip install Flask
- Run the file and the out put .ttl file displayed in "http://localhost:5000/cadata"
- For windo os to see the ttl format ctrl+u
- for Mac os to see the ttl format ctr+option+u

** Posting the generated file **

- Creat LDP container https://territoire.emse.fr/ldp
- Give the link to the created container 
- run the code 
* In our case:
- Here we make a post by giving the container we created in Territoire LDP which is: https://territoire.emse.fr/ldp/sararandika2/ 
- It generate spesiffic UID for each event 
- User can take one given UID to look at specific event

** Query the graph **

- Query the graph is GET_EVENTS which uses a sparql query to fetch events occurring on a specific date (as specific by the user) from the LDP.
- Query an event 
  1 Get the first 10 subject,pridicate,object from our graph 
  2 Get the subject,pridicate,object from all graph 
  3 Get spesific course given the name of the course
  4 Get the up comming events


# Validation
* Installation
  -Install with PIP (Using the Python3 pip installer pip3)
   $ pip3 install pyshacl
- Or in a python virtualenv (these example commandline instructions are for a Linux/Unix based OS)
  - $ python3 -m virtualenv --python=python3 --no-site-packages .venv
  - $ source ./.venv/bin/activate
  - $ pip3 install pyshacl 

- To validte if the generated graph in a proper shape
- Use EVENT.ttl file as shacl_file 
- Give the generated calander graph
- Run the validate.py

----------------------------------


# 2. Execution

Generating calender turtle file
To run this application, simply run the TTL_File_Generator.py file. This will
generate a calender turtle (ttl) file on the given path on your machine (you should
change the existing path in the code to your path) and start up web server in localhost
5000 port to display the result. You should route on http://localhost:5000/cadata to get the result

# NOTE: The result in the web server will be in JSON format so to change to ttl: - ctrl + U ------for Windo OS
- Cmd + U------for Mac

Posting the generated file
Create LDP container which the linked data could be stored. We created https://territoire.emse.fr/ldp/sararandika2
Give the link to the created container in the code and the generated ttl file then simply
run the Post.py file


Go to your container and it will create different UID for each event and you can cheak
the event e.g https://territoire.emse.fr/ldp/sararandika2/b19e5d68-9d6d-4b20-8a69-

Query the data in the graph using SPARQL
To get the result for specific query simply run Query_Result_cheaker.py file
And it will get SPARQL query one py one in your consule. E.g if you query for the subject pridicate object from specific graph:
sparql.setQuery(""" SELECT * FROM <https://territoire.emse.fr/ldp/sararandika2/>
WHERE { ?subj ?pre ?ob. }
LIMIT 10
"""
)


Validation
We use SHACL to enhance the semantic and technical interoperability layers of the
generated graph. To validate the generated graph,include the generated ttl file in your working
directory and give the path of the ttl file in the code also give the right path of the
EVENT.ttl file (which should be included in the project while you downloaded it
since we included it already), then run validate.py file. NOTE: EVENT.ttl file is a schema that we used as a reference to validate our
generated graph. We choose to use it because we are validating the event.
