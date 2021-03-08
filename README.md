Exploratory Data Analysis
[![Generic badge](https://img.shields.io/badge/Offline_View-Open-Blue.svg)](https://nbviewer.jupyter.org/github/BruSunshine/manufacturing_costs_prediction/blob/main/project_eda.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/BruSunshine/manufacturing_costs_prediction/blob/main/project_eda.ipynb)

Machine Learning
[![Generic badge](https://img.shields.io/badge/Offline_View-Open-Blue.svg)](https://nbviewer.jupyter.org/github/BruSunshine/manufacturing_costs_prediction/blob/main/project_ml.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/BruSunshine/manufacturing_costs_prediction/blob/main/project_ml.ipynb)

## What does this project do ?
----- 
It is a cost prediction model for parts produced in a manufacturing workshop.

## Why is this project useful?
-----
There are many such shops, and many persons involved in the calculations process each time, spending precious time in manual calculations and guessing.
Such a cost prediction system helps the business:  
- by enabeling short reaction time in front of a client. 
- by securing the margin of a project.
- by decreasing the risk level associated.
- by quantifiying and keeping records of the non-written knowledge contained in the company as group of individuals.
- by bringing transparency on the numbers and costs drivers.

## How do I get started?
-----

If I am a contributor:

If I am interested in building a deep learning model to detect features from technical drawings I can look at this [here](https://github.com/BruSunshine/features_extractor_2Dpdf/blob/main/README.md)  
We need improvement on this one.

if I am interested in CAD systems and I want to improve the features extraction I can look at this one [here](https://github.com/BruSunshine/features_extractor_3Dstep/blob/main/README.md)  

If I am a potential user and would like to apply such a model in my company I can open a discussion to discuss how it could be deployed in a specific field.  

## Where can I get more help, if I need it?
-----
 Yes sure .. I need to write smth here ..


## predict_manufacturing_costs
Data pipeline from features extraction to target prediction

### 1) The problem

We work in partnership with a virtual metal manufacturing company called MY_COMPANY.

**MY_COMPANY**  

MY_COMPANY is a manufacturer in the field of mechanics. They specialize in the engineering, design, and construction of components and subassemblies in metal.

**Offering**  

The complex assemblies offered by MY_COMPANY typically include metallic components machined and assembled, modified by any special process. The products range from (1gram, 1mm) up to (10kg,1m). The complexity is given by the number of parts assembled, up to 30 components, the tolerence levels required on the invidual components, which can be as fine as 0.001mm.
MY_COMPANY produces prototypes and series of parts ranging from a few and up to several hundred of units. The parts as highly customized, requiering strong internal engineering capabilities.

**Activities**  

The critical components are produced at MY_COMPANY, the non-critical ones as well as spezialized special processes such as coating, paintings or heat treatments are bought on the market.
MY_COMPANY operates several different machining centers as wells as assembling and measuring equipments.

**Our goal**  

We want to support MY_COMPANY in their finance and controlling activities.
One important aspect of such a company is to be able to issue rapidely technical and commercial offers to their customers, with a sufficient level of precision, a low level of risk, and a financial margin secured. This requires a strong ability to define the costs prognose at the project start.
The prediction activity is a complex task, depending from a large number of parameters, typically performed by highly experienced professionals able to anticipate the full project costs.
The costs evaluation they produced is usually composed of a rational part issued from various calculations, their 'feeling' from experience, their appetence to risk.
Our project offers to help them performing this anticipation work by bringing more rational into it.

**Current situation**  

We recognize that the offers issued by the tendering managers are numerous, up to several hundred a year.
The offers contain typically a part description, a production process, and leads to a part unit cost.
The offers are calculated from scratch each time, leading to a high usage of ressources, high dependence on individuals, low level of capitalization on experience. 

**Proposed situation**  

Each of those offers could be modeled as a vector of parameters (our features), corresponding to a costs (our target). Some well known machine learning algorithm are used to learn from the past available information and make proposals in new offering conditions. Those recommendations are used as reference point by the tendering managers to build their offers, or to generate quick offers based on a limited set of typical parameters available at project start.

**Traduction of the problem in data science terms**  

This is a regression problem where the features are the technical parameters of the production order and the target is the cost of the production order.  

**Discussion**  

We want to learn from past information to predict new projects costs:
- We can do this because we have labeled data generated by the tendering professionals over the years.
- This is not a final step in such: The ideal case would be to learn from the actually executed projects and incurred costs, with given project parameters, in order to predict new project conditions. Here the labelling would be performed by the entiere company in real world data conditions.
- We could also add to the target the cycle time for the part.

### 2) The data

##### Data source

The full matrix of features and target(s) is build as a combination from multiple sources detailed below: 1,2,3  

The source of information are the principal documents the tendering manager will be using during the project. We try to extract as much as possible features from them. The extraction of features is driven by intuition that some feature could represent a meaningful information for the target prediction, even if the impact seems indirect or not massive.

N = x000 is the cardinality of the training set available.  
D > 250 is the dimension of our features matrix.  

Note that we developped extraction technics to get features from the 3 sources:

1. Custom calculation sheets or export from the company ERP system as *.xlsx or *.csv files from which we will generate features matrix shape (N,<185)  
Note: Data extration depends from the data structure available from MY_COMPANY.

2. Technical part drawings as \*.pdf from which we will generate features matrix shape (N,<50)  
See documentation [here](https://github.com/BruSunshine/features_extractor_2Dpdf/blob/main/README.md)

3. Technical part 3D models as *.step from which we will generate features matrix shape (N,<100)  
See documentation [here](https://github.com/BruSunshine/features_extractor_3Dstep/blob/main/README.md)



