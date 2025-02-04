# Bootstrap 5 WordPress Navbar Walker

[![Build Status](https://badgen.net/github/checks/fiskhandlarn/bootstrap-5-wordpress-navbar-walker?label=build&icon=github)](https://github.com/fiskhandlarn/bootstrap-5-wordpress-navbar-walker/actions)
[![Total Downloads](https://badgen.net/packagist/dt/fiskhandlarn/bootstrap-5-wordpress-navbar-walker)](https://packagist.org/packages/fiskhandlarn/bootstrap-5-wordpress-navbar-walker)
[![Latest Version](https://badgen.net/packagist/v/fiskhandlarn/bootstrap-5-wordpress-navbar-walker)](https://packagist.org/packages/fiskhandlarn/bootstrap-5-wordpress-navbar-walker)
[![License](https://badgen.net/packagist/license/fiskhandlarn/bootstrap-5-wordpress-navbar-walker)](https://packagist.org/packages/fiskhandlarn/bootstrap-5-wordpress-navbar-walker)

## Installation

Require this package, with [Composer](https://getcomposer.org), in the root directory of your project.

```bash
$ composer require fiskhandlarn/bootstrap-5-wordpress-navbar-walker
```

## Usage

1. Register a new menu by adding the follow code into the functions.php file of your theme:
```php
register_nav_menu('main-menu', 'Main menu');
```
2. Add the following html code in your header.php file or wherever you want to place your menu:
```php
<nav class="navbar navbar-expand-lg bg-light">
  <div class="container-fluid">
    <a class="navbar-brand" href="#">Navbar</a>
    <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarSupportedContent" aria-controls="navbarSupportedContent" aria-expanded="false" aria-label="Toggle navigation">
      <span class="navbar-toggler-icon"></span>
    </button>
    <div class="collapse navbar-collapse" id="navbarSupportedContent">
<?php
     wp_nav_menu([
         'theme_location' => 'navigation',
         'container' => false,
         'menu_class' => '',
         'fallback_cb' => '__return_false',
         'items_wrap' => '<ul id="%1$s" class="navbar-nav me-auto mb-2 mb-lg-0 %2$s">%3$s</ul>',
         'depth' => 2,
         'walker' => new Fiskhandlarn\Bootstrap5WordpressNavbarWalker(),
     ]);
?>
    </div>
  </div>
</nav>
```

### Add support for [dropdown menu (responsive) alignment](https://getbootstrap.com/docs/5.0/components/dropdowns/#menu-alignment)

- From _Appearance -> Menus_ page of WordPress, check the _CSS Classes_ checkbox under _Screen Options_;
- Add a _Custom Link_ with "#" in the URL field (this would be the parent of your dropdown);
- On the _CSS Classes_ field add any of the following alignment classes: 'dropdown-menu-start', 'dropdown-menu-end', 'dropdown-menu-sm-start', 'dropdown-menu-sm-end', 'dropdown-menu-md-start', 'dropdown-menu-md-end', 'dropdown-menu-lg-start', 'dropdown-menu-lg-end', 'dropdown-menu-xl-start', 'dropdown-menu-xl-end', 'dropdown-menu-xxl-start', 'dropdown-menu-xxl-end';
- If any of the mentioned above class is detected, then they will automatically copied into the _ul.dropdown-menu_ element following the Bootstrap 5 structure;
- Any other class that is not related to the dropdown menu alignment will stay where it is.

## License
[Expat License](./LICENSE)
