<properties
	pageTitle="Code Styles"
	description=""
	authors="bursteg"
	tags="cla" />

# Code Styles

## Xml
<pre class="prettyprint lang-xml">
<configuration>
    <appSettings>
        <add key="StorageConnectionString" value="DefaultEndpointsProtocol=https;AccountName=storagesample;AccountKey=nYV0gln9fT7bvY+rxu2iWAEyzPNITGkhM88J8HUoyofpK7C8fHcZc2kIZp6cKgYRUM74lHI84L50Iau1+9hPjB==" />
    </appSettings>
</configuration>
</pre>

## C#
<pre class="prettyprint lang-csharp">
// Retrieve storage account from connection string.
CloudStorageAccount storageAccount = CloudStorageAccount.Parse(
    CloudConfigurationManager.GetSetting("StorageConnectionString"));

// Create the blob client.
CloudBlobClient blobClient = storageAccount.CreateCloudBlobClient();

// Retrieve reference to a previously created container.
CloudBlobContainer container = blobClient.GetContainerReference("mycontainer");

// Retrieve reference to a blob named "myblob".
CloudBlockBlob blockBlob = container.GetBlockBlobReference("myblob");

// Create or overwrite the "myblob" blob with contents from a local file.
using (var fileStream = System.IO.File.OpenRead(@"path\myfile"))
{
    blockBlob.UploadFromStream(fileStream);
}
</pre>

## Json
<pre class="prettyprint lang-json">
{
    "$schema": "http://json-schema.org/schemas/2014-11-01/apiapp.json#",
    "id": "ContactsList",
    "namespace": "microsoft.com",
    "gateway": "2015-01-14",
    "version": "1.0.0",
    "title": "ContactsList",
    "summary": "",
    "author": "",
    "endpoints": {
        "apiDefinition": "/swagger/docs/v1",
        "status": null
    },
    "authentication": [{"type": "aad"}]
}
</pre>

## Console
```bash
azure-storage@0.5.0 node_modules\azure-storage
+-- extend@1.2.1
+-- xmlbuilder@0.4.3
+-- mime@1.2.11
+-- node-uuid@1.4.3
+-- validator@3.22.2
+-- underscore@1.4.4
+-- readable-stream@1.0.33 (string_decoder@0.10.31, isarray@0.0.1, inherits@2.0.1, core-util-is@1.0.1)
+-- xml2js@0.2.7 (sax@0.5.2)
+-- request@2.57.0 (caseless@0.10.0, aws-sign2@0.5.0, forever-agent@0.6.1, stringstream@0.0.4, oauth-sign@0.8.0, tunnel-agent@0.4.1, isstream@0.1.2, json-stringify-safe@5.0.1, bl@0.9.4, combined-stream@1.0.5, qs@3.1.0, mime-types@2.0.14, form-data@0.2.0, http-signature@0.11.0, tough-cookie@2.0.0, hawk@2.3.1, har-validator@1.8.0)
```

## Python
<pre class="prettyprint lang-python">
blobs = []
marker = None
while True:
    batch = blob_service.list_blobs('mycontainer', marker=marker)
    blobs.extend(batch)
    if not batch.next_marker:
        break
    marker = batch.next_marker
for blob in blobs:
    print(blob.name)
</pre>

## Java
<pre class="prettyprint lang-java">
try
{
    // Retrieve storage account from connection-string.
    CloudStorageAccount storageAccount = CloudStorageAccount.parse(storageConnectionString);

    // Create the blob client.
    CloudBlobClient blobClient = storageAccount.createCloudBlobClient();

   // Retrieve reference to a previously created container.
    CloudBlobContainer container = blobClient.getContainerReference("mycontainer");

    // Define the path to a local file.
    final String filePath = "C:\\myimages\\myimage.jpg";

    // Create or overwrite the "myimage.jpg" blob with contents from a local file.
    CloudBlockBlob blob = container.getBlockBlobReference("myimage.jpg");
    File source = new File(filePath);
    blob.upload(new FileInputStream(source), source.length());
}
catch (Exception e)
{
    // Output the stack trace.
    e.printStackTrace();
}
</pre>

## Objective-C
<pre class="prettyprint lang-objective-c">
 -(void)createContainer{
    // Create a storage account object from a connection string.
    AZSCloudStorageAccount *account = [AZSCloudStorageAccount accountFromConnectionString:@"DefaultEndpointsProtocol=https;AccountName=your_account_name_here;AccountKey=your_account_key_here"];

    // Create a blob service client object.
    AZSCloudBlobClient *blobClient = [account getBlobClient];

    // Create a local container object.
    AZSCloudBlobContainer *blobContainer = [blobClient containerReferenceFromName:@"newcontainer"];

    // Create container in your Storage account if the container doesn't already exist
    [blobContainer createContainerIfNotExistsWithCompletionHandler:^(NSError *error, BOOL exists) {
        if (error){
            NSLog(@"Error in creating container.");
        }
    }];
}
</pre>