# Custom Debian ARM Image for Oracle Cloud Infrastructure

April 22, 2023

## Download Debian ARM Image

1.  Go to **[https://cloud.debian.org/images/cloud/bullseye/latest/](https://cloud.debian.org/images/cloud/bullseye/latest/)**
2.  Download **debian-11-genericcloud-arm64.qcow2**

## Creating a Bucket

If you already have a bucket, you can choose to use it instead and continue to [Uploading Debian ARM Image](#uploading-debian-arm-image).

To create a bucket to store objects:
1. Open the navigation menu and click **Storage**. Under **Object Storage**, click **Buckets**
2. Click **Create Bucket**
3. In the **Create Bucket** dialog box, specify the attributes of the bucket:
	- **Bucket Name:** Name the bucket e.g. **Images**
	- **Default Storage Tier:** Select **Standard**
	- **Encryption:** Select **Encrypt using Oracle managed keys**
4. Click **Create**

## Uploading Debian ARM Image

1. Open the navigation menu and click **Storage**. Under **Object Storage**, click **Buckets**
2. Click on the bucket you want to upload to
3. Click **Upload**
4. In the **Upload Objects** dialog, select the file **debian-11-genericcloud-arm64.qcow2** from your computer
5. Click **Upload**
6. Click **Close**

## Creating Custom Debian ARM Image

1. Open the navigation menu and click **Compute**. Under **Compute**, click **Custom Images**
2. Click **Import image**
3. In the **Import image** dialog:
	- **Name:** Enter a name for the image
	- **Operating system** 
		- Select **Linux**
		- Select the **Import from an Object Storage bucket** option
	- **Bucket in ... :** Locate the bucket that you uploaded the image to, select the bucket
	- **Object name:** Select the image file that you uploaded
	- **Image type:** Select **QCOW2**
	- **Launch mode:** Select **Paravirtualized mode**
4. Click **Import image**.

The imported image appears in the **Custom images**, with a state of **Importing**. When the import completes successfully, the state changes to **Available**.

## Adapting Custom Debian ARM Image

1. Open the navigation menu and click **Compute**. Under **Compute**, click **Custom Images**
2. Click on the custom Debian ARM image
3. Click **Edit details**
4. In the **Edit image details** dialog, select only **VM.Standard.A1.Flex**
5. Click **Save changes**
6. Click **Edit image capabilities**
7. In the **Edit image capabilities** dialog:
	- **Firmware:** Select only **UEFI_64**
	- **Launch mode:** Select only **CUSTOM**
8. Click **Save changes**

## Remember

After you create an instance with the custom Debian ARM image, use the username **debian** when logging in with ssh.

## References

- https://docs.oracle.com/en-us/iaas/Content/Object/Tasks/managingbuckets_topic-To_create_a_bucket.htm
- https://docs.oracle.com/en-us/iaas/Content/Object/Tasks/managingobjects_topic-To_upload_objects_to_a_bucket.htm
- https://docs.oracle.com/en-us/iaas/Content/Compute/Tasks/importingcustomimagelinux.htm#linux
- https://cloudgal42.com/installing-debian-on-oci/
- https://www.reddit.com/r/oraclecloud/comments/rxjpil/comment/ixix3oi/?utm_source=share&utm_medium=web2x&context=3