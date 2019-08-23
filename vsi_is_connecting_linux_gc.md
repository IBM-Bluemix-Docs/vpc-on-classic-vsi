---

copyright:
  years: 2018, 2019
lastupdated: "2018-11-14"

keywords: private key, IP address, instance, Linux instance, ssh key, connect to your instance, connect to your linux instance, connect to your virtual server
subcollection: vpc-on-classic-vsi

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:pre: .pre}
{:tip: .tip}
{:table: .aria-labeledby="caption"}

# Connecting to your Linux instance
{: #connecting-to-your-linux-instance}

After you have created your {{site.data.keyword.vsi_is_full}} Linux instance, you can connect to it with your SSH key by completing these steps.
{:shortdesc}

## Locating floating IP address
{: #locating-floating-ip-address}

If you need to locate your floating IP address for the instance to which you want to connect, complete the following steps. If you already know your floating IP address, you can skip to [Getting connected](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-connecting-to-your-linux-instance#getting-connected). 

1. You need to identify your floating IP ID before you can locate your floating IP address. Run the following command to identify your floating IP ID:

   ```
   $ ibmcloud is instance-network-interfaces <INSTANCE_ID> --json
   ```
   {:codeblock}

   For this example, you'd see a response similiar to the following output (using generic x and 123 values for example purposes only):

   ```
   "floating_ips": [
           {
               "crn:v1:mydomain:public:vpc:us-south:a/c4cxxxc10xx54xxx9e2xxx59xxx3fa0f::floating_ip:12345x67-8901-234x-5678-9xx01xx23x4x",
               "href": "https://us-south.myaccount.cloud.ibm.com/v1/floating_ips/12345x67-8901-234x-5678-9xx01xx23x4x",
               "id": "12345x67-8901-234x-5678-9xx01xx23x4x",
               "name": “my-instance”
           }
       ]
   ```
   {:screen}  

2. Now that you have your floating IP ID, you can locate your floating IP address by running the following command.

   ```
   $ ibmcloud is ip <FLOATING_IP_ID>
   ```
   {:codeblock}

   For this example, you'd see a response similiar to the following output (using generic x and 123 values for example purposes only):

   ```
   ID               12345x67-8901-234x-5678-9xx01xx23x4x   
   Address          123.45.678.90   
   Name             my-instance   
   Target           primary(1xx2x34x-.)   
   Target Type      intf   
   Target IP        12.345.6.78   
   Created          1 week ago   
   Status           available   
   Zone             us-south-1   
   Resource Group   -   
   Tags             -   
   ```
   {:screen}

Optionally, you can locate the floating IP address associated to the instance to which you want to connect through the {{site.data.keyword.cloud_notm}} console.
{:tip}

## Getting connected
{: #getting-connected}

The values returned below are for example purposes only.

1. To connect to your instance, use your private key and run the following command:

   ```
   $ ssh -i <path to your private key file> root@<floating ip address>
   ```
   {:codeblock}

   You receive a response similar to the following example. When prompted to continue connecting, type `yes`.
   ```
   The authenticity of host 'xxx.xxx.xxx.xxx (xxx.xxx.xxx.xxx)' can't be established.
   ECDSA key fingerprint is SHA256:abcdef1Gh/aBCd1EFG1H8iJkLMnOP21qr1s/8a3a8aa.
   Are you sure you want to continue connecting (yes/no)? yes
   Warning: Permanently added 'xxx.xxx.xxx.xxx' (ECDSA) to the list of known hosts.
   ```
   {:screen}

   You are now accessing your server.

2. When you are ready to end your connection, run the following command:

   ```
   # exit
   ```
   {:codeblock}

## Next steps
{: #next-managing-instances}

After you are connected to your instance, you can [manage your instances using the {{site.data.keyword.cloud_notm}} console](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-managing-virtual-server-instances#managing-virtual-server-instances) or [manage your instances using the CLI](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-managing-virtual-servers-cli#managing-virtual-servers-cli).
