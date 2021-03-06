


*   In order to support and expand the core functionality of carapace we develop a companion module called **carapace_defaults** and a set of importable configurations (**carapace_defaults_demo**). \
 \
Carapace_defaults relies on several third party modules which are enforced as install dependencies, modules with an * are nice to have but not required for full functionality, each module has notes on why it was added.
    *   block_class:block_class (adds custom classes for blocks from the UI) *
    *   Twig_tweak:twig_tweak (used to render facets inside the view)
    *   Formatter_suite:formatter_suite (adds text formatter options) *
    *   Context_groups:context_groups (Groups context blocks) *
    *   Config_split:config_split (Generate configuration splits) *
    *   Condition_query:condition_query (Not used but present in config) *
    *   At_tools:at_tools (Required by carapace)
    *   Addtoany:addtoany (Social Icons)
    *   Term_condition:term_condition (Allows context to filter by term)
    *   Content_sync:content_sync (Allows to export content, not used) *
    *   Config_ignore:config_ignore (Ignore configurations) *
    *   Ds:ds (display suite enables display override per node/entity and title options)
    *   ds:ds_extras
    *   ds:ds_switch_view_mode
    *   File_download_link:file_download_link (Creates the download link on objects)
    *   Fixed_block_content:fixed_block_content (Block content exportables)
    *   Conditional_fields:conditional_fields (not used but present in configuration) *
    *   Views_conditional:views_conditional (not used but present in configuration) *
*   Before enabling carapace_defaults, it has to be included as a composer dependency. Also make sure you are running our fork of the Carapace theme. Here’s how we recommend doing that:

1. Add both as VCS external packages:

```
    "repositories": [
       # ... existing definitions ...
       {
           "type": "vcs",
           "url": "https://github.com/Born-Digital-US/carapace.git"
       },
              {
           "type": "vcs",
           "url": "https://github.com/Born-Digital-US/carapace-defaults.git"
       }
    ],
```

2. And then you need to make sure your “require” statement specifies the correct branch for both repositories:
```
    "require": {
        # ... lots of other requirements
        "islandora/carapace": "dev-born-digital_fork",
        "islandora/carapace-defaults": "dev-master",
    }
```
3. Run composer update to have these changes take effect.

*   The module has its own composer file, when included as a dependency of the project, composer will fetch all of the required dependencies automatically

    Carapace_defaults will attempt upon install to enable configurations to create new elements such as context, view modes, view tweaks and more if the configuration install fails (which is common when other conflicting configurations exists), it is advised to resolve those conflicts by hand, there are two possible options 1 delete the offending configuration from the config/install folder, or move the install folder to some other location and apply changes individually using either drush or drupal console.


    Additionally  carapace_defaults_config_demo defines a set of GLOBAL configuration overrides for Islandora and Drupal in the form of a Feature. In general it is advisable NOT to install it over a previously configured site, it is present as way to quickly set up a brand new site and enable most Carapace features. Enabling this submodule will override some Islandora Defaults configurations.

*   carapace_defaults provides the following enhancements over to carapace
    *   Blank /home route to create homepages
    *   Removes exposed filters from default solr_search from search
    *   Enables custom solr_search header (sort/pagination/grid/list)
    *   Adds Compound objects and its related components (views/themes/ajax/viewmode)
    *   Tweaks Collection (view/viewmode/theme)
    *   Defines Items in Collection Field
    *   Defines Entity Reference Count Formatter
    *   Defines General Use ajax view render block
    *   Adds new libraries (CSS/JS) to support it
    *   Adds new OpenSeaDragon Field to render openseadragon viewer
    *   Modifies solr_content_search to render facets automatically as attachments before view gets rendered
    *   Defines Permalink field to show the permanent URL of an object
    *   Supplies configurations to tweak existing and new islandora configurations to alter layouts, field order and more.
*   To install just do `drush en -y carapace_defaults` or though the UI. See note above regarding when and how to install `carapace_defaults_demo`. 
