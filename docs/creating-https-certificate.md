You can either create your certificates by
[makecert](http://msdn.microsoft.com/en-us/library/bfsktky3%28v=vs.80%29.aspx)
or by [OpenSSL](http://www.openssl.org/). And this [How to Setup a
CA](http://pages.cs.wisc.edu/~zmiller/ca-howto/) gives you an easy
tutorial of creating certificates hierarchy by **OpenSSL**. First is the
root CA certificate. For experimental cases, **makecert** is enough. But
for product, you may want to use **OpenSSL** or apply a certificate from
CA like VeriSign.

```cmd
makecert -n "CN=TestCA" -r -sv TestCA.pvk TestCA.cer
```

And import the root certificate to the system certificate storage of
Trusted Root Certification Authority. [See this
article](http://www.codeproject.com/Articles/25677/Simple-WCF-X509-Certificate).

Then create the certificate for your HTTPS web site.

```cmd
makecert -iv TestCA.pvk -n "CN=TestSite" -sv TestSite.pvk -ic TestCA.cer TestSite.cer -sr LocalMachine -ss My -sky exchange --pe
```

If you will test your client app on a machine other than the server
machine, you have to import the **TestCA.cer** to the client machine as
well. So that the client machine trust **TestCA** (the root cert), it
will also trust the server certificate (**TestSite**).

Hosting an HTTPS site, you must have a certificate with private key. But
the last **makecert** command creates the private key in **TestCA.pvk**
which can't be imported to the system storage directly. We have to
convert it to **.pfx** format

```cmd
pvk2pfx -pvk "TestSite.pvk" -spc "TestSite.cer" -pfx "TestSite.pfx"
```

You have to import **TestSite.pfx** into the Local Computer Personal
Certificate store.