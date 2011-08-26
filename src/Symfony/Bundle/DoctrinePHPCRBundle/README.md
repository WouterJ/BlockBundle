# Doctrine PHPCR Bundle

This bundle integrates Doctrine PHPCR ODM and PHPCR backends like Jackalope or
Midgard2 CR into Symfony2.

It is part of the [symfony-cmf](https://github.com/symfony-cmf/symfony-cmf)
repository and additionally exposed standalone repository in case you do not
want the rest of the symfony-cmf bundles.

**Never commit to the standalone repository.** All commits and pull requests go
to the main repository https://github.com/symfony-cmf/symfony-cmf
Maintainers: See docs/StandaloneBundles.md for how to update the standalone
repository.


# Installation

### With symfony-cmf

Please see the main README at https://github.com/symfony-cmf/symfony-cmf

### Standalone

* Grab this repository and [Doctrine PHPCR ODM](http://github.com/doctrine/phpcr-odm) into your Symfony project
* Add `Symfony\Bundle\DoctrinePHPCRBundle\DoctrinePHPCRBundle` to your Kernel's registerBundles() method
* Add autoloader for Doctrine\PHPCR, Doctrine\ODM\PHPCR and Doctrine\Bundle namespaces


## Configuration

The configuration is similar to Doctrine ORM and MongoDB configuration for Symfony2 as its based
on the AbstractDoctrineBundle aswell:

    doctrine_phpcr:
        # configure the PHPCR session
        session:
            backend:
                url: http://localhost:8080/server/
            workspace: default
            username: admin
            password: admin
        # enable the ODM layer
        odm:
            auto_mapping: true

## Services

You can access the PHPCR services like this:

    <?php

    namespace Acme\DemoBundle\Controller;

    use Symfony\Bundle\FrameworkBundle\Controller\Controller;

    class DefaultController extends Controller
    {
        public function indexAction()
        {
            // PHPCR session instance
            $session = $this->container->get('doctrine_phpcr.default_session');
            // PHPCR ODM document manager instance
            $documentManager = $this->container->get('doctrine_phpcr.odm.default_document_manager');
        }
    }