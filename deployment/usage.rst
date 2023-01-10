Usage
========

We will cover following operations using the CLI tool:

* Listing of Datasets(also known as processes) Information
* Download entries from the the UDCP
* Append entry to the Datasets to the UDCP


List of Available Commands:
-------------------------
To see the list of available options invoke the executable help command:
  ..  code-block:: console
    
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

An example execution of the command is shown below:

 ..  code-block:: console

    $ java -jar leap-cli.jar process -l

    2023-01-10 10:07:04.894  INFO 96134 --- [           main] e.v.e.secretapp.EnigmaApplicationKt      : Starting EnigmaApplicationKt using Java 17.0.2 on isislab with PID 96134 (/Users/yogeshbarve/Projects/rest-tutorials/enigma/secretapp/build/libs/secretapp-0.0.1-SNAPSHOT.jar started by yogeshbarve in /Users/yogeshbarve/Projects/rest-tutorials/enigma/secretapp/build/libs)
    2023-01-10 10:07:04.899  INFO 96134 --- [           main] e.v.e.secretapp.EnigmaApplicationKt      : The following profiles are active: device
    2023-01-10 10:07:06.657  INFO 96134 --- [           main] e.v.e.secretapp.EnigmaApplicationKt      : Started EnigmaApplicationKt in 2.6 seconds (JVM running for 3.654)
    2023-01-10 10:07:09.641  INFO 96134 --- [           main] common.util                              : 
    [ {
    "description" : "test for CWL demo holding patient cohort",
    "processId" : "bdas77ab-15b3-48bf-8c15-3259278b25c4",
    "processType" : "TestSim",
    "function" : false
    }, {
    "description" : "CWL patient cohort data",
    "processId" : "71ecb2312-c13e-48ee-b2ed-a067c646f1ae",
    "processType" : "TestSim",
    "function" : false
    },]

Description:
 
The processId is the unique identifier for the process. 
The processType is the type of process. 
The description is the description of the process. 
The function is a boolean value that indicates whether the process is a function or not.

Download Data
--------------

To find the usage of the command execute following command:

.. code-block:: console

    $java -jar leap-cli.jar download -h
    2023-01-10 10:27:50.464  INFO 96591 --- [           main] e.v.e.secretapp.EnigmaApplicationKt      : Starting EnigmaApplicationKt using Java 17.0.2 on isislab with PID 96591 (/Users/yogeshbarve/Projects/rest-tutorials/enigma/secretapp/build/libs/secretapp-0.0.1-SNAPSHOT.jar started by yogeshbarve in /Users/yogeshbarve/Projects/rest-tutorials/enigma/secretapp/build/libs)
    2023-01-10 10:27:50.470  INFO 96591 --- [           main] e.v.e.secretapp.EnigmaApplicationKt      : The following profiles are active: device
    2023-01-10 10:27:52.135  INFO 96591 --- [           main] e.v.e.secretapp.EnigmaApplicationKt      : Started EnigmaApplicationKt in 2.411 seconds (JVM running for 3.199)
    Usage: <main class> download [-hm] -d=<dir> [-i=<obsIndex>] [-o=<observerID>]
                                -p=<processID> [-t=<token>]
    -d, --dir=<dir>          Directory Path
    -h, --help               Utility for Test Commandline Options...
    -i, --index=<obsIndex>   Observer ID
    -m, --metadata           Download all Observations(without datafiles)
    -o, --oid=<observerID>   Observer ID
    -p, --process=<processID>
                            ProcessID
    -t, --token=<token>      Auth Token to pass when using Auth Passthrough Mode!


To download the data from the content repositories we would need the unique identifier of the repository (process) which can be found from the previous step.

.. code-block:: console

    $java -jar leap-cli.jar download -p 06ae4327-ad66-4608-b1eb-3655a5342d67 -d ./output

    2023-01-10 10:24:21.288  INFO 96510 --- [           main] e.v.e.secretapp.EnigmaApplicationKt      : Starting EnigmaApplicationKt using Java 17.0.2 on isislab with PID 96510 (/Users/yogeshbarve/Projects/rest-tutorials/enigma/secretapp/build/libs/secretapp-0.0.1-SNAPSHOT.jar started by yogeshbarve in /Users/yogeshbarve/Projects/rest-tutorials/enigma/secretapp/build/libs)
    2023-01-10 10:24:21.292  INFO 96510 --- [           main] e.v.e.secretapp.EnigmaApplicationKt      : The following profiles are active: device
    2023-01-10 10:24:22.832  INFO 96510 --- [           main] e.v.e.secretapp.EnigmaApplicationKt      : Started EnigmaApplicationKt in 2.101 seconds (JVM running for 2.601)
    2023-01-10 10:24:25.588  INFO 96510 --- [           main] common.services.TaxonomyServerClient     : URL: http://welcmewebgme.centralus.cloudapp.azure.com
    2023-01-10 10:24:29.289  INFO 96510 --- [           main] command.DownloadCmd                      : Waiting for transfer to start.... 
    2023-01-10 10:24:29.892  INFO 96510 --- [           main] command.DownloadCmd                      : .
    2023-01-10 10:24:31.405  INFO 96510 --- [           main] command.DownloadCmd                      : .
    2023-01-10 10:24:32.827  INFO 96510 --- [           main] command.DownloadCmd                      : .
    2023-01-10 10:24:34.161  INFO 96510 --- [           main] command.DownloadCmd                      : .
    2023-01-10 10:24:54.266  INFO 96510 --- [           main] command.DownloadCmd                      : .
    2023-01-10 10:24:54.266  INFO 96510 --- [           main] command.DownloadCmd                      : Download started.. 
    2023-01-10 10:24:54.268  INFO 96510 --- [           main] common.services.FileDownloader           : Current file: /Users/yogeshbarve/Projects/rest-tutorials/enigma/secretapp/build/libs/output/dat/1/metadata.json
    2023-01-10 10:24:54.470  INFO 96510 --- [           main] common.services.FileDownloader           : Remote File size 276
    2023-01-10 10:24:54.473  INFO 96510 --- [           main] common.services.FileDownloader           : Local File Size 276
    2023-01-10 10:24:54.618  INFO 96510 --- [           main] common.services.FileDownloader           : Current file: /Users/yogeshbarve/Projects/rest-tutorials/enigma/secretapp/build/libs/output/dat/1/database.db
    2023-01-10 10:24:55.088  INFO 96510 --- [           main] common.services.FileDownloader           : Remote File size 570281984
    2023-01-10 10:24:55.088  INFO 96510 --- [           main] common.services.FileDownloader           : Local File Size 570281984


Upload Data
--------------
To find the usage of the command execute following command:

.. code-block:: console

    $java -jar leap-cli.jar push -h
    2023-01-10 10:34:44.240  INFO 96763 --- [           main] e.v.e.secretapp.EnigmaApplicationKt      : Starting EnigmaApplicationKt using Java 17.0.2 on isislab with PID 96763 (/Users/yogeshbarve/Projects/rest-tutorials/enigma/secretapp/build/libs/secretapp-0.0.1-SNAPSHOT.jar started by yogeshbarve in /Users/yogeshbarve/Projects/rest-tutorials/enigma/secretapp/build/libs)
    2023-01-10 10:34:44.244  INFO 96763 --- [           main] e.v.e.secretapp.EnigmaApplicationKt      : The following profiles are active: device
    2023-01-10 10:34:45.584  INFO 96763 --- [           main] e.v.e.secretapp.EnigmaApplicationKt      : Started EnigmaApplicationKt in 1.913 seconds (JVM running for 2.409)
    Usage: <main class> upload [-h] -d=<dir> [-f=<metadata>] [-o=<observerID>]
                            -p=<processID> [-t=<token>] [-validate -type=<type>
                            -path=<path>]
    -d, --dir=<dir>          Directory Path
    -f=<metadata>            JSON file path of metadata for the observation
    -h, --help               Utility for Test Commandline Options...
    -o, --oid=<observerID>   Observer ID
    -p, --process=<processID>
                            ProcessID
    -path=<path>         Taxonomy input source path - (file path/ URL address)
    -t, --token=<token>      Auth Token to pass when using Auth Passthrough Mode!
        -type=<type>         Taxonomy input source can be either of type either
                                url or file
        -validate


To perform upload operation to the UDCP repositories one could execute following example command:


.. code-block:: console
    
    java -jar leap-cli.jar upload -p 06aewe7-ad66-4608-b1eb-3655a5342d67 -f  ./input/metadata.json -d ./input


Description:
Here `-f` points to the metadata file.
`-d` points to the input directory to be uploaded to the content repository.
