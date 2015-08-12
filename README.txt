*****************************************
*
* App: Splunk Add-on for SurfWatch Labs API
* Current Version: 1.0
* Last Modified: Aug 2015
* Splunk Version: 6.x
* Author: SurfWatch Labs
*
*****************************************

**** Overview ****

The Splunk Add-on for SurfWatch Labs API provides a few basic examples for consuming
data from the SurfWatch Labs API and ingesting it into Splunk.  A dashboard is provided
to show various ways to leverage the CyberFacts.


**** Quick Start Guide ****

Before you start, you will need a valid app_id and app_key pair from https://www.surfwatchlabs.com/
in order to access the SurfWatch Labs API.  With these you can configure the Splunk Add-on.

Also note that the primary intention of this add-on is to highlight how to get data from
the SurfWatch Labs API into your Splunk instance.  A variety of factors specific to your
environment (Splunk license indexing rates, single vs distributed indexes, data needs,
accounting for Splunk downtime, etc) may require you to tweak settings.  For questions you can
always contact support@surfwatchlabs.com.

** Searching CyberFacts **
By default all of the collection scripts will populate an index called 'swl_cyberfacts'.  Once
you ingest some data you should be able to see it by searching 'index=swl_cyberfacts' or by
using the 'Search for CyberFacts' timeline navigation item.

** Visualizing CyberFacts **
A sample dashboard is provided to show various ways to visualize CyberFact data.  The data is filtered
by Industry so make sure to select different industries to explore the data.  By default the Industry
selected is Consumer Goods.

** Collecting CyberFacts **
The easiest way to get started is to leverage the provided 'get_cyberfacts.py' input script.
If enabled (Settings > Data Inputs > Scripts > get_cyberfacts.py > Enable), this script will poll
the SurfWatch Labs API once a day in the middle of the night (GMT).  You can always adjust when it
is run through the Splunk UI (Settings > Data Inputs > Scripts > get_cyberfacts.py > click) or by
modifying inputs.conf.

** Backfilling & Collecting CyberFacts **
If you'd like to backfill your index, that is, get all historical CyberFacts there is a provided
'backfill_cyberfacts.py' script.  If you enable (Settings > Data Inputs > Scripts > backfill_cyberfacts.py > Enable )
this script it will begin running and starting from yesterday, get a days worth of data,
sleep for a few seconds, and then get another days worth of data backwards in time.  This script is
meant to be enabled around the same time as 'get_cyberfacts.py' so that no data gaps should occur.
Note that once this script finishes gathering data you will need to disable it so that it does
not get executed again.

** Collecting CyberFacts in realtime **
To truly collect CyberFacts in realtime you will need to leverage the SurfWatch Labs Realtime API.
This will require you to allow incoming POST requests from SurfWatch Labs into your Splunk environment
to an endpoint you configure.  For more information please see https://www.surfwatchlabs.com/ or
contact support@surfwatchlabs.com.

**** Release Notes ****

v1.0: Aug 2015
  - Initial release
