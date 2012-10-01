TCPDFBundle
=======================

This bundle facilitates easy use of the TCPDF PDF generation library in
Symfony2 applications.

Installation
------------

### Step 1: Add the bundle to your composer.json
``` yaml
# composer.json
{
    # ...
    "require": {
        # ...
        "wrep/tcpdf-bundle" : "dev-master"
    }
}    
```

### Step 2: Run Composer update

Run Composer's ``update`` to install the TCPDF library and TCPDF Bundle:

```bash
$ php composer.phar update
```

### Step 3: Enable the bundle in the kernel

Add the bundle to the `registerBundles()` method in your kernel:

``` php
<?php
// app/AppKernel.php

public function registerBundles()
{
    $bundles = array(
        // ...
        new Wrep\TCPDFBundle\WrepTCPDFBundle(),
    );
}
```

Using TCPDF
-----------

You can obtain the `wrep.tcpdf` service from the container,
and then create a new TCPDF object via the service:

``` php
$pdfObj = $container->get("wrep.tcpdf")->create();
```

From hereon in, you are using a TCPDF object to work with as normal.

Troubleshooting
---------------

If you experience errors while deploying to a production environment, make sure to clean the cache:

```bash
php app/console cache:clear --env=prod
```

Using a custom class
--------------------

If you want to use your own custom TCPDF-based class, you can use
the `class` parameter in your configuration eg in `config.yml`:

``` yaml
wrep_tcpdf:
    class: 'Acme\MyBundle\MyTCPDFClass'
```

The class must extend from the `TCPDF` class; an exception will be
thrown if this is not the case.

