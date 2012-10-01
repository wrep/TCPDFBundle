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

Configuration
-------------

### Basic configuration

``` yaml
wrep_tcpdf:
    file: '%kernel.root_dir%/../vendor/tcpdf/tcpdf/tcpdf.php'
    class: 'TCPDF'
    tcpdf:
        k_path_url: '%kernel.root_dir%/../vendor/tcpdf/tcpdf'
        k_path_main: '%kernel.root_dir%/../vendor/tcpdf/tcpdf/'
        k_path_fonts: '%kernel.root_dir%/../vendor/tcpdf/tcpdf/fonts/'
        k_path_cache: '%kernel.cache_dir%/tcpdf/tcpdf'
        k_path_url_cache: '%kernel.cache_dir%/tcpdf/tcpdf'
        k_path_images: '%kernel.root_dir%/../vendor/tcpdf/tcpdf/images/'
        k_blank_image: '%kernel.root_dir%/../vendor/tcpdf/tcpdf/images/_blank.png'
        k_cell_height_ratio: 1.25
        k_title_magnification: 1.3
        k_small_ratio: 0.666666
        k_thai_topchars: true
        k_tcpdf_calls_in_html: false
        k_tcpdf_external_config: true
        head_magnification: 1.1
        pdf_page_format: 'A4'
        pdf_page_orientation: 'P'
        pdf_creator: 'TCPDF'
        pdf_author: 'TCPDF'
        pdf_header_title: ''
        pdf_header_string: ''
        pdf_header_logo: ''
        pdf_header_logo_width: ''
        pdf_unit: 'mm'
        pdf_margin_header: 5
        pdf_margin_footer: 10
        pdf_margin_top: 27
        pdf_margin_bottom: 25
        pdf_margin_left: 15
        pdf_margin_right: 15
        pdf_font_name_main: 'helvetica'
        pdf_font_size_main: 10
        pdf_font_name_data: 'helvetica'
        pdf_font_size_data: 8
        pdf_font_monospaced: 'courier'
        pdf_image_scale_ratio: 1.25
```

### Using a custom class

If you want to use your own custom TCPDF-based class, you should use
the `class` parameter in your configuration file:

``` yaml
wrep_tcpdf:
    class: 'Acme\MyBundle\MyTCPDFClass'
```

The class must extend from the `TCPDF` class; an exception will be
thrown if this is not the case.

