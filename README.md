Python chatbot AI that helps in creating a python based chatbot with minimal coding. This provides both bots AI and chat handler and also allows easy integration of REST API's and python function calls which makes it unique and more powerful in functionality. This AI provides numerous features like learn, memory, conditional switch, topic-based conversation handling, etc.\



Installation

Install from PyPI:

pip install chatbotAI
install from github:


cd Chatbot
python setup.py install
Demo


@register_call("whoIs")
def who_is(session, query):
    try:
        return wikipedia.summary(query)
    except Exception:
        for new_query in wikipedia.search(query):
            try:
                return wikipedia.summary(new_query)
            except Exception:
                pass
    return "I don't know about "+query

first_question="Hi, how are you?"
Chat("examples/Example.template").converse(first_question)
For Detail on how to build Facebook messenger bot checkout Facebook Integration.ipynb

For Jupyter notebook Chatbot checkout Infobot built using NLTK-Chatbot

Sample Apps

A sample facebook messenger bot built using messengerbot, Django and NLTK-Chatbot is available here Facebook messenger bot
A sample microsoft bot built using Microsoft Bot Connector Rest API - v3.0, Django and NLTK-Chatbot is available here Micosoft Chatbot
List of feature supported in bot template

Memory
Get matched group
Recursion
Condition
Change Topic
Interact with python function
REST API integration
Topic based group
Learn
To upper case
To lower case
Capitalize
Previous
Memory

Set Memory

{ variable : value }
In think mode

{! variable : value }
Get Memory

{ variable }
Get matched group

for grouping in regex refer Python regular expression docs

Get Nth matched group of client pattern

%N
Example to get first matched

%1
Get matching named group of client pattern

%Client_pattern_group_name
Example to get matching named group person

%person
Get Nth matched group of bots message pattern

%!N
Example to get first matched

%!1
Get matching named group of bots message pattern

%!Bot_pattern_group_name
Example to get matching named group region

%!region
Recursion

Get response as if client said this new statement

{% chat statement %}
It will do a pattern match for statement

Condition

{% if condition %} do this first {% elif condition %} do this next {% else %} do otherwise {% endif %}
Change Topic

{% topic TopicName %}
Interact with python function

In python

@register_call("functionName")
def function_name(session, query):
    return "response string"
In template

{% call functionName: value %}
REST API integration

In API.json file


If authentication is required only then auth method is needed.The data and params defined in pi.json file acts as defult values and all key value pair defined in template file overrides the default value.value_getter consistes of list of keys in order using which info from json will be collected.

In Template file

[ APIName:MethodName,Key1:value1 (,Key*:value*) ]
you can have any number of key value pair and all key value pair will override data or params depending on method, if method is POST then it overrides data and if method is GET then it overrides params.


