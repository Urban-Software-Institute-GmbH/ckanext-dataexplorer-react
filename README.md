## Table of Contents
1. [Forked Description](#1-forked-description)
2. [Features](#2-features)
3. [Installation](#3-installation)
4. [Development Installation](#4-development-installation)


[![CKAN](https://img.shields.io/badge/ckan-2.8-orange.svg?style=flat-square)](https://github.com/ckan/ckan/tree/2.8) [![CKAN](https://img.shields.io/badge/ckan-2.9-orange.svg?style=flat-square)](https://github.com/ckan/ckan/tree/2.9)

### 1. Forked Description

🚨🚨 This repository was forked from https://github.com/keitaroinc/ckanext-dataexplorer-react

The original plugin was missing some view-related files when used with CKAN 2.11.4, specifically: dataexplorer/fantastic/webassets.yml

This caused the following error:

`ERROR [ckan.lib.webassets_tools] Trying to include unknown asset: dataexplorer/main`


To resolve this issue, I updated the MANIFEST.in file to include *.yml and *.yaml files so that they are properly packaged and included when building the Python distribution. 🚨🚨



### 2. Features

A Data Explorer app for CKAN built in React:

* Preview data from DataStore in a table.
  * Set predefined filters.
  * Set suggested filters.
* Filter data using SQL-like query builder which calls `datastore_search_sql` API.
* Build charts and maps similar to classic Data Explorer but with improved UI/UX.

![ezgif-3-2c8e3c18ac8e](https://user-images.githubusercontent.com/17809581/121645171-b33ddf80-cab5-11eb-8680-b98ddea353b3.gif)

### 3. Installation

**Important notice:** if you're using CKAN >v2.8.6 or >v2.9.1 you need to make sure that `over` function of Postgresql is enabled via `datastore_search_sql` endpoint. To do so you may need to add it into your allow list here - https://github.com/ckan/ckan/blob/master/ckanext/datastore/allowed_functions.txt

The React code repository is here - https://github.com/datopian/data-explorer.

To install ckanext-dataexplorer-react:

I. Activate your CKAN virtual environment, for example::

     . /usr/lib/ckan/default/bin/activate

II. Install the ckanext-dataexplorer-react Python package into your virtual environment::
   `pip install -e git+https://github.com/datopian/ckanext-dataexplorer-react.git#egg=ckanext-dataexplorer-react`

III. Add ``dataexplorer_view`` to the ``ckan.plugins`` setting in your CKAN
   config file (by default the config file is located at
   ``/etc/ckan/default/production.ini``)
    * `dataexplorer_view`for multiview visualization table, chart and map.
    * Add `dataexplorer_table_view` for table view.
    * Add `dataexplorer_chart_view` for chart view.
    * Add `dataexplorer_map_view` for map view.
    * Add `dataexplorer_web_view` for external web view.

IV. Restart CKAN. For example if you've deployed CKAN with Apache on Ubuntu::

     sudo service apache2 reload


### 4. Development Installation


To install ckanext-dataexplorer-react for development, activate your CKAN virtualenv and
do::

    git clone https://github.com/datopian/ckanext-dataexplorer-react.git
    cd ckanext-dataexplorer-react
    python setup.py develop
    pip install -r dev-requirements.txt

