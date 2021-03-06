=================
Logentries Logger
=================

This is a plugin library to enable logging to Logentries from the Python Logger. Logentries is a real-time log management service on the cloud. More info at https://logentries.com.

Setup
-----

To use this library, you must first create an account on Logentries. This will only take a few moments.

Install
-------

To install this library, use the following command:

`pip install logentries`

Usage
-----

    #!/usr/bin/env python
    
    import logging
    from logentries import LogentriesHandler

    log = logging.getLogger('logentries')

    test = LogentriesHandler(LOGENTRIES_TOKEN, block_on_flush=True)

    log.addHandler(test)
	log.setLevel(logging.INFO)    #WARN by default
    log.warn("Warning message")

Configure
---------

To ensure that all log messages are sent to Logentries before closing the handler, set `block_on_flush=True` in the constructor. The default is false, which means that unsent log messages are discarded.

The parameter `LOGENTRIES_TOKEN` needs to be filled in to point to a file in your Logentries account.

In your Logentries account, create a new host, giving it a name that represents your app. Then create a logfile, selecting `Token TCP` as the source_type. This will print a Token UUID
beside the logfile. This is the value to use for `LOGENTRIES_TOKEN`.

You are now ready to start logging
