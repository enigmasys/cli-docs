Usage
========

We will cover following operations using the CLI tool:

* Listing of Datasets(also known as processes) Information
* Download records from the the UDCP
* Upload records to the content repository on the UDCP


List of Available Commands:
-------------------------
To see the list of available options invoke the executable help command:
  ..  code-block:: console
    
    $java -jar leap_cli.jar -h
    Usage: <main class> [-hV] [-t=<token>] [COMMAND]
    Command for accessing the UDCP
    -h, --help            Show this help message and exit.
    -t, --token=<token>   Auth Token to pass when using Auth Passthrough Mode!
    -V, --version         Print version information and exit.
    Commands:
    upload, push
    process, proc, repository, repo
    download, pull
    userinfo, user

Login
------

To access the UDCP, we are required to login to the UDCP. To login to the UDCP, we need to login through the browser using the following user command option.
Help listing for the user command can be invoked using the following command:

  ..  code-block:: console

    $java -jar leap_cli.jar user -h
    Usage: <main class> userinfo [-hosV] [-t=<token>]
    -h, --help              Show this help message and exit.
    -o, --logout            Logout from this Application
    -s, --login, --status   Display the Status of this Application/User.
    -t, --token=<token>     Auth Token to pass when using Auth Passthrough Mode!
    -V, --version           Print version information and exit.

To login issue following command:

 .. code-block:: console

    $java -jar leap_cli.jar user --login
    To sign in, use a web browser to open the page https://microsoft.com/devicelogin and enter the code FPP2356LE to authenticate.
        {
    "userId" : "qweaf4-asdwae-49bd-9997-asd345",
    "permission" : "Administrator",
    "administrator" : false,
    "registrationApprover" : false
    }

The user will need to provide the code displayed on the console to the browser to login to the UDCP. Accept any security permissions asked.
If the user has the required permission to the UDCP, the user will be logged in successfully.

When logged successfully, the user information is stored in the currently running folder of the leap_cli.jar executable directory.

To logout issue following command:

    .. code-block:: console

        $java -jar leap_cli.jar user --logout
        Login Functionality..
        User Logged out successful
    

Dataset Listing
--------------

To list the content repositories, use the following command:

An example execution of the command is shown below:

 ..  code-block:: console

    $ java -jar leap_cli.jar repo -l
    =============================================
    Repository ID                         | Content Type | Description              | Is Function
    9b119f79-69de-4278-ba8e-df9953e3ab9e  |  demodataset  |  Demo1  |  false
    87dc1607-5d63-4073-9424-720f86ecef43  |  demoworkflow  |  WorkflowDemo1  |  false
    6e9da372-8cc7-4b11-bf85-23ed9d83a301  |  vutest  |  TestRepo1  |  false
    ae0f62d0-854b-4696-8c7d-54e89e04308e  |  vutest  |  TestRepo2  |  false
    dbad238e-287c-4515-b89f-740a2e5b57d5  |  vutest  |  TestRepo3  |  false
    0e86da05-f79a-48fa-8776-de5f5b2b00aa  |  vutest  |  TestRepo4  |  false
    0d215d9f-1f5b-4a61-b63b-af3c37a85da0  |  vutest  |  TestRepo5  |  false
    7ef2f867-27de-436a-bee0-af2c65cdd1b3  |  SADemo  |  Input patient cohort for the suicide attemtp example  |  false
    =============================================
Description:
 
The Repository ID is the unique identifier for the process. 
The Content Type is the content type name for the repository. 
The description is the description of the process. 
The function is a boolean value that indicates whether the process is a function or not.



Download Data
--------------
To find the usage of the command execute following command:

.. code-block:: console

    $java -jar leap_cli.jar download -h
    Usage: <main class> download [-hm] -d=<dir> [-i=<obsIndex>] -p=<processID>
                                [-t=<token>]
    -d, --dir=<dir>          Directory Path
    -h, --help               Helps in downloading of records from a repository.
    -i, --index=<obsIndex>   index of the record
    -m, --metadata           Download ONLY all metadata files (without the data
                                files)
    -p, -repo, --process=<processID>
                            Repository ID (a.k.a. ProcessID) of the repository
    -t, --token=<token>      Auth Token to pass when using Auth Passthrough Mode!



.. To see the existing metadata records available in the content repository, we could issue following 
.. command with the associated directory path to which we can download the metadata to.

.. .. code-block:: console

..     $java -jar leap_cli.jar download -m -p 6e9da372-8cc7-4b11-bf85-23ed9d83a301 -d ./output
    
..     Saving metadata to /Users/Downloads/output/metadata/0/metadata.json
..     {
..     "displayName" : "WorkflowDemo1",
..     "taxonomyVersion" : {
..         "branch" : "master",
..         "id" : "AllLeap+TaxonomyBootcamp",
..         "url" : "wellcomewebgme.centralus.cloudapp.azure.com"
..     }
..     }
..     Saving metadata to /Users/Downloads/output/metadata/1/metadata.json
..     {
..     "displayName" : "WorkflowDemo1",
..     "taxonomyTags" : [ {
..         "DPActigraphy" : {
..         "collectionPeriod" : {
..             "End DateTime" : "1",
..             "Frequency" : "1",
..             "Start DateTime" : "1"
..         }
..         }
..     } ],
..     "taxonomyVersion" : {
..         "branch" : "master",
..         "id" : "AllLeap+TaxonomyBootcamp",
..         "url" : "wellcomewebgme.centralus.cloudapp.azure.com"
..     }
..     }
..     Saving metadata to /Users/Downloads/output/metadata/2/metadata.json
..     {
..     "displayName" : "WorkflowDemo1",
..     "taxonomyTags" : [ {
..         "DPActigraphy" : {
..         "collectionPeriod" : {
..             "End DateTime" : "1",
..             "Frequency" : "1",
..             "Start DateTime" : "1"
..         }
..         }
..     } ],
..     "taxonomyVersion" : {
..         "branch" : "master",
..         "id" : "AllLeap+TaxonomyBootcamp",
..         "url" : "wellcomewebgme.centralus.cloudapp.azure.com"
..     }
..     }



To download the data from the content repositories we would need the unique identifier of the repository (repository ID) which can be found from the previous step.

.. code-block:: console

    $java -jar leap_cli.jar download -p 6e9da372-8cc7-4b11-bf85-23ed9d83a301 -d ./output -i 14
    Saving metadata to /Users/Downloads/output/metadata/14/metadata.json
    Download Command Invoked.
    =====================================
    Downloading records from repository 6e9da372-8cc7-4b11-bf85-23ed9d83a301
    Waiting for transfer to start....
    Download started..
    .............Downloading file: /Users/Downloads/output/dat/14/assembly_summary_genbank.txt
    Remote File size 111678605
    Starting Download..
    Finished Downloading file: /Users/Downloads/output/dat/14/assembly_summary_genbank.txt
    Downloading file: /Users/Downloads/output/dat/14/test/assembly_summary_refseq_historical.txt
    Remote File size 2818004
    Starting Download..
    Finished Downloading file: /Users/ /Downloads/output/dat/14/test/assembly_summary_refseq_historical.txt
    Downloading file: /Users/Downloads/output/dat/14/test/assembly_summary_genbank_historical.txt
    Remote File size 3188527
    Starting Download..
    Finished Downloading file: /Users/ /Downloads/output/dat/14/test/assembly_summary_genbank_historical.txt
    Downloading file: /Users/ /Downloads/output/dat/14/assembly_summary_refseq.txt
    Remote File size 51436481
    Starting Download..
    Finished Downloading file: /Users/ /Downloads/output/dat/14/assembly_summary_refseq.txt
    Downloading file: /Users/ /Downloads/output/dat/14/test/assembly_summary_genbank.txt
    Remote File size 111678605
    Starting Download..
    Finished Downloading file: /Users/ /Downloads/output/dat/14/test/assembly_summary_genbank.txt
    Downloading file: /Users/ /Downloads/output/dat/14/test/assembly_summary_refseq.txt
    Remote File size 51436481
    Starting Download..
    Finished Downloading file: /Users/ /Downloads/output/dat/14/test/assembly_summary_refseq.txt
    Downloading file: /Users/ /Downloads/output/dat/14/assembly_summary_refseq_historical.txt
    Remote File size 2818004
    Starting Download..
    Finished Downloading file: /Users/ /Downloads/output/dat/14/assembly_summary_refseq_historical.txt
    Downloading file: /Users/ /Downloads/output/dat/14/assembly_summary_genbank_historical.txt
    Remote File size 3188527
    Starting Download..
    Finished Downloading file: /Users/ /Downloads/output/dat/14/assembly_summary_genbank_historical.txt
    =====================================
    Download Operation Completed
    =====================================
    ~/Downloads$

We can now check the directory structure of the downloaded data.

.. code-block:: console

    ~/Downloads$tree ./output
    ./output
    ├── dat
    │   └── 14
    │       ├── assembly_summary_genbank.txt
    │       ├── assembly_summary_genbank_historical.txt
    │       ├── assembly_summary_refseq.txt
    │       ├── assembly_summary_refseq_historical.txt
    │       └── test
    │           ├── assembly_summary_genbank.txt
    │           ├── assembly_summary_genbank_historical.txt
    │           ├── assembly_summary_refseq.txt
    │           └── assembly_summary_refseq_historical.txt
    └── metadata
        ├── 0
        │   └── metadata.json
        ├── 1
        │   └── metadata.json
        ├── 10
        │   └── metadata.json
        ├── 11
        │   └── metadata.json
        ├── 12
        │   └── metadata.json
        ├── 13
        │   └── metadata.json
        ├── 14
        │   └── metadata.json
        ├── 2
        │   └── metadata.json
        ├── 3
        │   └── metadata.json
        ├── 4
        │   └── metadata.json
        ├── 5
        │   └── metadata.json
        ├── 6
        │   └── metadata.json
        ├── 7
        │   └── metadata.json
        ├── 8
        │   └── metadata.json
        └── 9
            └── metadata.json

    19 directories, 23 files


Upload Data
--------------
To find the usage of the command execute following command:

.. code-block:: console

    $java -jar leap_cli.jar upload -h
    Usage: <main class> upload [-h] -d=<dir> [-f=<metadata>] -p=<processID>
                            [-t=<token>]
    -d, --dir=<dir>       Directory Path
    -f=<metadata>         JSON file path of metadata for the record
    -h, --help            Helps in uploading of records to a repository.
    -p, -repo, --process=<processID>
                            Repository ID (a.k.a. ProcessID) of the repository
    -t, --token=<token>   Auth Token to pass when using Auth Passthrough Mode!


To perform upload operation to the UDCP repositories one could execute following example command:


.. code-block:: console
    
    $java -jar leap_cli.jar upload -p 6e9da372-8cc7-4b11-bf85-23ed9d83a301 -d ./output/dat/14/ -f ./output/metadata.json
    Upload Command Invoked.
    =====================================
    Uploading records from output/dat/14 to repository 6e9da372-8cc7-4b11-bf85-23ed9d83a301
    Uploading File: output/dat/14/test/assembly_summary_refseq_historical.txt
    Finished Uploading: output/dat/14/test/assembly_summary_refseq_historical.txt
    Uploading File: output/dat/14/test/assembly_summary_refseq.txt
    Finished Uploading: output/dat/14/test/assembly_summary_refseq.txt
    Uploading File: output/dat/14/test/assembly_summary_genbank_historical.txt
    Finished Uploading: output/dat/14/test/assembly_summary_genbank_historical.txt
    Uploading File: output/dat/14/test/assembly_summary_genbank.txt
    Finished Uploading: output/dat/14/test/assembly_summary_genbank.txt
    Uploading File: output/dat/14/assembly_summary_refseq_historical.txt
    Finished Uploading: output/dat/14/assembly_summary_refseq_historical.txt
    Uploading File: output/dat/14/assembly_summary_refseq.txt
    Finished Uploading: output/dat/14/assembly_summary_refseq.txt
    Uploading File: output/dat/14/assembly_summary_genbank_historical.txt
    Finished Uploading: output/dat/14/assembly_summary_genbank_historical.txt
    Uploading File: output/dat/14/assembly_summary_genbank.txt
    Finished Uploading: output/dat/14/assembly_summary_genbank.txt
    Upload Complete
    =====================================

Description:
Here `-f` points to the metadata file.
`-d` points to the input directory to be uploaded to the content repository.


Check the CLI Version
--------------

To check the version of the CLI tool, issue following command:

.. code-block:: console

    $java -jar leap_cli.jar -V
    Current CLI Version is: v0.1.0
    Checking for updates...
    ===========================================
    Latest Release: v0.1.0  was published at: 2023-08-29T20:55:38Z
    Latest Release can be found at https://github.com/enigmasys/enigma/releases/tag/v0.1.0
    This CLI version is up to date.
    ===========================================
    Current CLI Version: v0.1.0
    Latest Release Version: v0.1.0

