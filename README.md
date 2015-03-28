# VIZBI 2015 Tutorial: Cytoscape, IPython, Docker and Reproducible Data Visualization Workflow

![](http://cl.ly/aPzx/duet1.jpg)

#### Release History
* 3/27/2015: Rev. 0.5.0.  Samples used in VIZBI tutorials

### Please read [this wiki](https://github.com/idekerlab/cyREST/wiki/VIZBI-2015-Tutorial) first!

## Introduction
This is the repository for the course material used in VIZBI 2015 tutorial session.  By following these lessons, you will learn:

* How to use basic features of [IPython Notebook](http://ipython.org/notebook.html) (or [Jupyter](http://jupyter.org/).  Essentially those two are the same.)
* Basics of RESTful API for Cytoscape ([cyREST](http://apps.cytoscape.org/apps/cyrest))
* Data round trip between cyREST-compatible JSON (same as the one used in Cytoscape.js. See the example below) and [NetworkX](https://networkx.github.io/)
* Simple data analysis with NetowrkX and other libraries (igraph and graph-tool)
* How to creaet reproducible data visualization scripts in Python 

# Quick Start Guide

## Required Software Pakcages
Make sure your machine has the following to run these notebooks:

* Git (Tested on 2.3.3)
* Docker (Tested on 1.5)

For cyREST tutorial part, you need the following:
* Latest version of Java 8
* [Cytoscape 3.2.1](http://www.cytoscape.org/download.php)
* [cyREST App](http://apps.cytoscape.org/apps/cyrest)

## Option 1: Run the container
If you just want to run these workflows, simply follow this instruction:

1. (Optional) Fork this repo to your own account
1. Clone this repo: ```git clone https://github.com/idekerlab/vizbi-2015.git```
1. ```cd vizbi-2015```
1. Run Docker image:
	```docker run -d -p 80:8888 -v $PWD:/notebooks -e "PASSWORD=you_can_use_your_own_pw" -e "USE_HTTP=1" idekerlab/vizbi-2015```
1. Mac & Windows users: If you use __boot2docker__ to run Docker commands, check the VM's IP address: ```boot2docker ip```
1. Open the URL: ```http://192.168.59.103``` or ```http://localhost```
1. Type your password and start rom _Lesson 0_ in _tutorials_ directory


## Option 2: Hack the container
If you want to edit the container image first, follow this instruction:

1. Fork this repo to your own account
1. Clone the repo you just forked to your account
1. cd into the dir
1. Edit ___Dockerfile___ and add whatever you want to add to this sample image
1. Build the image: ```docker build -t cyrest-tutorials .```
1. Run Docker image:
	```docker run -d -p 80:8888 -v $PWD:/notebooks -e "PASSWORD=you_can_use_your_own_pw" -e "USE_HTTP=1" cyrest-tutorials```
1. Follow the instruction above from #4


For more information and backgrounds, please read [this page](https://github.com/idekerlab/cyREST/wiki/VIZBI-2015-Tutorial).

----

### Sample Cytoscape.js style object
```javascript
{
	data: {name: 'network_name'},
	elements: {
    nodes: [
      { data: { id: 'foo' } }, // NB no group specified

      { data: { id: 'bar' } },

      {
        data: { weight: 100 }, // elided id => autogenerated id 
        group: 'nodes',
        position: {
          x: 100,
          y: 100
        },
      }
    ],

    edges: [
      { data: { id: 'baz', source: 'foo', target: 'bar' } } // NB no group specified
    ]
  }
}
```

## Questions?
Send them to me (kono ucsd edu).