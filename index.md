---

copyright:
  years: 2018, 2019
lastupdated: "2019-10-11"

Keywords: IBM Cloud Hyper Protect Crypto Services, getting started, example, dedicated key management service, IBM Key, Key storage, HSM, cloud hardware security module

subcollection: hs-crypto

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:important: .important}
{:tip: .tip}
{:external: target="_blank" .external}

# Getting started with {{site.data.keyword.cloud_notm}} {{site.data.keyword.hscrypto}}
{: #get-started}

{{site.data.keyword.cloud}} {{site.data.keyword.hscrypto}} ({{site.data.keyword.hscrypto}} for short) is a dedicated key management service and hardware security module (HSM). It is designed to enable you to take control of your cloud data encryption keys and cloud hardware security modules, and is the only service in the industry built on FIPS 140-2 Level 4-certified hardware.
{:shortdesc}

{{site.data.keyword.hscrypto}} integrates with {{site.data.keyword.keymanagementservicefull_notm}} API to generate and encrypt keys. The Keep Your Own Keys (KYOK) function is also enabled by {{site.data.keyword.hscrypto}} to provide access to cryptographic hardware that is FIPS 140-2 Level 4 certified technology, the highest level attainable of security.

{{site.data.keyword.hscrypto}} offers network addressable HSMs and is accessible via [Enterprise PKCS#11 (EP11)](/docs/services/hs-crypto?topic=hs-crypto-enterprise_PKCS11_overview) application programming interface (API). <!-- You can access {{site.data.keyword.hscrypto}} via an Advanced Cryptography Service Provider (ACSP) client, which communicates with the ACSP server to enable you to access the backend cryptographic resources.-->  Applications can access {{site.data.keyword.hscrypto}} remotely by calling EP11 API through frameworks such as [gRPC](https://grpc.io/){: external}. For more information about {{site.data.keyword.hscrypto}}, see [{{site.data.keyword.hscrypto}} overview](/docs/services/hs-crypto?topic=hs-crypto-overview). For more information about security requirements for cryptographic modules, see [the specification of the NIST for FIPS 140-2 Level](https://csrc.nist.gov/publications/detail/fips/140/2/final){: external}.

<!-- {{site.data.keyword.hscrypto}} is the cryptography that {{site.data.keyword.blockchainfull_notm}} Platform is built with. It is also a member of the {{site.data.keyword.cloud_notm}} Hyper Protect Family, including [{{site.data.keyword.cloud_notm}} Hyper Protect DBaaS](https://cloud.ibm.com/docs/services/hypersecure-dbaas/index.html){: external}, {{site.data.keyword.cloud_notm}} {{site.data.keyword.hscrypto}}, [{{site.data.keyword.cloud_notm}} Container Service](https://cloud.ibm.com/docs/containers/container_index.html){: external}, and [{{site.data.keyword.cloud_notm}} {{site.data.keyword.hsplatform}}](https://cloud.ibm.com/docs/services/hypersecure-platform/index.html){: external}. -->

This tutorial guides you how to set up your service instance by managing your master keys, and create and add existing cryptographic keys by using the {{site.data.keyword.hscrypto}} dashboard.


## Step 1: Provision the service
{: #provision-service}

Before you begin, you must create an instance of {{site.data.keyword.hscrypto}} from the {{site.data.keyword.cloud_notm}} console. For detailed steps, see [Provisioning the service](/docs/services/hs-crypto?topic=hs-crypto-provision).

## Step 2: Initialize your service instance
{: #initialize-crypto}

To manage your keys, you need to initialize your service instance first. For a quick getting-started tutorial, see [Getting started with service instance initialization](/docs/services/hs-crypto?topic=hs-crypto-get-started-hsm). For detailed steps and best practices, see [Initializing service instances](/docs/services/hs-crypto?topic=hs-crypto-initialize-hsm).

## Step 3: Manage your data and keys
{: #manage-data-key}

### 1. Manage your keys through key management service
{: #manage-keys}

From the {{site.data.keyword.hscrypto}} dashboard, you can create new root keys or standard keys for cryptography, or you can import your existing keys. For more information on root keys and standard keys, see [Key management service components and concepts](/docs/services/hs-crypto?topic=hs-crypto-understand-concepts#key-management-concepts).

#### Creating new keys
{: #create-keys}

Complete the following steps to create your first cryptographic key.

1. From the {{site.data.keyword.hscrypto}} dashboard, click **Manage** &gt; **Add key**.
2. To create a new key, select **Generate key**.

    Specify the key's details:

    <table>
      <tr>
        <th>Setting</th>
        <th>Description</th>
      </tr>
      <tr>
        <td>Key type</td>
        <td>The type of key that you would like to manage in {{site.data.keyword.hscrypto}}.</td>
      </tr>
      <tr>
        <td>Name</td>
        <td>
          <p>A unique, human-readable alias for easy identification of your key.</p>
          <p>To protect your privacy, ensure that the key name does not contain personally identifiable information (PII), such as your name or location.</p>
        </td>
      </tr>
      <caption style="caption-side:bottom;">Table 1. Description of the <b>Create a key</b> settings</caption>
    </table>

3. When you are finished filling out the key's details, click **Add key** to confirm.

Keys that are created in the service are symmetric 256-bit keys, supported by the AES-CBC algorithm. For added security, keys are generated by FIPS 140-2 Level 4 certified hardware security modules (HSMs) that are located in secure {{site.data.keyword.cloud_notm}} data centers.

#### Importing your own keys
{: #import-keys}

You can enable the security benefits of Bring Your Own Key (BYOK) by bringing your existing keys to the service.

Complete the following steps to add an existing key.

1. From the {{site.data.keyword.hscrypto}} dashboard, click **Manage** &gt; **Add key**.
2. To upload an existing key, select **Use existing key**.

    Specify the key's details:

    <table>
      <tr>
        <th>Setting</th>
        <th>Description</th>
      </tr>
      <tr>
        <td>Key type</td>
        <td>The type of key that you would like to manage in {{site.data.keyword.hscrypto}}.</td>
      </tr>
      <tr>
        <td>Name</td>
        <td>
          <p>A unique, human-readable alias for easy identification of your key.</p>
          <p>To protect your privacy, ensure that the key name does not contain personally identifiable information (PII), such as your name or location.</p>
        </td>
      </tr>
      <tr>
        <td>Key material</td>
        <td>The key material, such as a symmetric key, that you want to store in the {{site.data.keyword.hscrypto}} service. The key that you provide must be base64 encoded.</td>
      </tr>
      <caption style="caption-side:bottom;">Table 2. Description of the <b>Import your own key</b> settings</caption>
    </table>

3. When you are finished filling out the key's details, click **Add key** to confirm.

From the {{site.data.keyword.hscrypto}} dashboard, you can inspect the general characteristics of your new keys.

### 2. Encrypte your data using Cloud HSM
{: #encrypt-data-hsm}

You can remotely access {{site.data.keyword.hscrypto}} Cloud HSM using EP11 over gRPC (GREP11). To perform cryptographic operations using GREP11 API, you need to generate a GREP11 API request, and pass the GREP11 API endpoint URL, service ID API key, IAM endpoint, and instance ID through the API call.

A [sample](https://github.com/ibm-developer/ibm-cloud-hyperprotectcrypto){:external} Github repository is provided for you to test the GREP11 API in Golang. GREP11 API supports programming languages with [gRPC libraries](https://developers.google.com/protocol-buffers/){:external}. In the [sample](https://github.com/ibm-developer/ibm-cloud-hyperprotectcrypto){:external} Github repository, only Golang code examples are provided.

Before you use the samples, perform the following tasks:
  1. Set up the Go environment:
    - [Install Go tools](https://golang.org/doc/install){:external}
    - [Set up your workspace directory](https://golang.org/doc/code.html#Workspaces){:external}
    - [Set the GOPATH environment variable](https://golang.org/doc/code.html#GOPATH){:external}
  2. Clone the [sample](https://github.com/ibm-developer/ibm-cloud-hyperprotectcrypto){:external} repository to the `$GOPATH/src/github.com/ibm-developer/` directory.


To run the sample code:

1. Update the following code snippet in the `server_test.go` file of the `src/github.com/ibm-developer/ibm-cloud-hyperprotectcrypto/golang/examples` directory:  

  ```Golang
  const address = "ep11.<region>.hs-crypto.cloud.ibm.com:<port>"

  var callOpts = []grpc.DialOption{
    grpc.WithTransportCredentials(credentials.NewTLS(&tls.Config{})),
    grpc.WithPerRPCCredentials(&util.IAMPerRPCCredentials{
      APIKey:   "<service_ID_API_key>",
      Endpoint: "https://iam.cloud.ibm.com",
      Instance: "<instance_ID>",
    }),
  }
  ```
  {: codeblock}

  In the code example,
  - Replace `<region>` and `<port>` with the value of your GREP11 API endpoint. To find the service endpoint URL, from your provisioned service instance dashboard, click **Manage**  &gt; **EP11 endpoint URL**.
  - Replace `<service_ID_API_key>` with the service ID API key that is created. The service ID API Key can be created by following the instruction in [Managing service ID API key](/docs/iam?topic=iam-serviceidapikeys){: external}.
  - Replace `<instance_ID>` with the instance ID that uniquely identified your service instance. Retrieve the instance ID that uniquely identifies your {{site.data.keyword.hscrypto}} service instance by following the instruction in [Retrieving your instance ID](/docs/services/hs-crypto?topic=hs-crypto-retrieve-instance-ID).

2. Change the directory with the following command:

  ```
  cd $GOPATH/src/github.com/ibm-developer/ibm-cloud-hyperprotectcrypto/golang/examples
  ```
  {: pre}

3. Execute the example by running the `go test -v` command.

  The sample program generates output similar to the following:
  ```Bash
	=== RUN   Example_getMechanismInfo
	--- PASS: Example_getMechanismInfo (0.02s)
	=== RUN   Example_encryptAndDecrypt
	--- PASS: Example_encryptAndDecrypt (0.03s)
	=== RUN   Example_digest
	--- PASS: Example_digest (0.02s)
	=== RUN   Example_signAndVerifyUsingRSAKeyPair
	--- PASS: Example_signAndVerifyUsingRSAKeyPair (0.66s)
	=== RUN   Example_signAndVerifyUsingECDSAKeyPair
	--- PASS: Example_signAndVerifyUsingECDSAKeyPair (0.04s)
	=== RUN   Example_signAndVerifyToTestErrorHandling
	--- PASS: Example_signAndVerifyToTestErrorHandling (0.04s)
	=== RUN   Example_wrapAndUnwrapKey
	--- PASS: Example_wrapAndUnwrapKey (0.65s)
	=== RUN   Example_deriveKey
	--- PASS: Example_deriveKey (0.11s)
	=== RUN   Example_tls
	--- PASS: Example_tls (0.05s)
	PASS
  ok  	github.com/ibm-developer/ibm-cloud-hyperprotectcrypto/golang/examples	1.667s
```

## What's next
{: #get-started-next}

- Now you can start to use your keys to encode your apps and services. If you added a root key to the service, you might want to learn more about using the root key to protect the keys that encrypt your at-rest data. Check out [Wrapping keys](/docs/services/hs-crypto?topic=hs-crypto-wrap-keys) to get started.
  - To find out more about managing and protecting your encryption keys with a root key, check out [Envelope encryption](/docs/services/hs-crypto?topic=hs-crypto-envelope-encryption).
  - To find out more about programmatically managing your keys, check out the [{{site.data.keyword.hscrypto}} key management API reference doc](https://{DomainName}/apidocs/hs-crypto){: external}.
- You can also manage and protect your data with {{site.data.keyword.hscrypto}}. To find out more about encrypting your data using the cloud HSM function of {{site.data.keyword.hscrypto}}, check out the [GREP11 API reference doc](/docs/services/hs-crypto?topic=hs-crypto-grep11-api-ref).
- To find out more about integrating the {{site.data.keyword.hscrypto}} service with other cloud data solutions, [check out the Integrations doc](/docs/services/hs-crypto?topic=hs-crypto-integrate-services).

<!-- ## Installing ACSP client libraries -->

<!-- You can access {{site.data.keyword.hscrypto}} via an Advanced Cryptography Service Provider (ACSP) client. Complete the following steps to install the ACSP client libraries in your local environment. -->

<!-- 1. Download the installation package from the [GitHub repository](https://github.com/ibm-developer/ibm-cloud-hyperprotectcrypto){: external}. In the **packages** folder, choose the installation package file that is suitable for your operation system and CPU architecture. For example, for Ubuntu on x86, choose `acsp-pkcs11-client_1.5-3.5_amd64.deb`.
2. Install the package to install the ACSP client libraries with the `dpkg` command. For example, `dpkg -i acsp-pkcs11-client_1.5-3.5_amd64.deb`. -->

<!-- ## Configuring ACSP client -->

<!-- At the current stage, {{site.data.keyword.hscrypto}} provides only self-signed certificates.

You need to configure the ACSP client to enable a proper secure communication channel (mutual TLS) to your service instance in the cloud. -->

<!-- 1. In your {{site.data.keyword.hscrypto}} service instance in {{site.data.keyword.cloud_notm}}, select **Manage** from the left navigator.
2. On the "Manage" screen, click the **Download Config** button to download the `acsp_client_credentials.uue` file.
3. Copy the `acsp_client_credentials.uue` file to the `/opt/ibm/acsp-pkcs11-client/config` directory in your local environment.
4. In the `/opt/ibm/acsp-pkcs11-client/config` directory, decode the file with the following command:
       `base64 --decode acsp_client_credentials.uue > acsp_client_credentials.tar`
5. Extract the client credentials file with the following command:
       `tar xf acsp_client_credentials.tar`
6. Move the `server-config` files into the default place with the following command:
       `mv server-config/* ./`
7. Rename the client credentials file with the following command:
       `mv acsp.properties.client acsp.properties`
8. (Optional:) Change group ID of the files with the following command:
       `chown root.pkcs11 *`
9. Enable ACSP to use the proper config for the service instance in the cloud:
       `export ACSP_P11=/opt/ibm/acsp-pkcs11-client/config/acsp.properties` -->

<!-- Now your ACSP client is operational and your {{site.data.keyword.hscrypto}} is ready to use!

For more information about ACSP client installation and configuration, see [ACSP Client Installation and Configuration Guide](https://github.com/ibm-developer/ibm-cloud-hyperprotectcrypto/blob/master/doc/ACSP-client-config-guide.pdf){: external}. -->
