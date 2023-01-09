Usage
========

We will cover following operations using the CLI tool:

* Listing of Datasets(also known as processes) Information
* Download entries from the the UDCP
* Append entry to the Datasets to the UDCP


List of Available Commands:
-------------------------
To see the list of available options invoke the executable help command:
    
        $ java -jar leap-cli.jar -h
    
        Usage: <main class> [-hV] [-t=<token>] [COMMAND]
            Command for UDCP CLI
            -h, --help            Show this help message and exit.
            -t, --token=<token>   Auth Token to pass when using Auth Passthrough Mode!
            -V, --version         Print version information and exit.
        Commands:
        upload, push
        process, proc
        download, pull
        userinfo, user
        dev, test







Dataset Listing
--------------

To list the content repositories, use the following command:

    $ java -jar leap-cli.jar process -l
