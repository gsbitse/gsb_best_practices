# GSB Best Practices

A place to document our standard operating procedures.

## Git
- Commit early, commit often.
- If you are working on a task that has an associated Jira ticket, please create a branch for the issue using the issue number as the name of the branch, for example, WP-100.
- Prefix your commits with the ticket number.
- Never prefix your commits with a `#` sign, this can cause the commit to be lost during rebase.
- Use `git add -p` to stage individual hunks, and use `git diff --staged` to review before committing.

## Dev environment

### Drush
- Use the 6.x branch of [drush](https://github.com/drush-ops/drush) from github

### Ruby
- Use [ruby-install](https://github.com/postmodern/ruby-install) and [chruby](https://github.com/postmodern/chruby) to manage ruby versions.
- Use [bundler](http://bundler.io) to manage rubygem versions.

## Drupal

### Site building
- Use [Display Suite](http://drupal.org/project/ds) when possible to alter the display of content

### Theming
- Avoid use of template (.tpl.php) files whenever possible
  - When overriding a template file, copy the original and rename as appropriate, and then commit it. Make the actual changes to the file in a separate commit.
- Favor preprocess hooks over theme functions over template files.

### Module dev
- Use [`entity_metadata_wrapper()`](http://drupalcontrib.org/api/drupal/contributions!entity!entity.module/function/entity_metadata_wrapper/7) whenever accessing field values on an entity.
- Use [`hook_ENTITYTYPE_view()`](http://api.drupal.org/api/search/7/hook_node_view) and [`hook_field_extra_fields()`](http://api.drupal.org/api/search/7/hook_field_extra_fields) to add non-field data to an entity
- Prefer [`hook_ENTITYTYPE_view_alter()`](http://api.drupal.org/api/search/7/hook_node_view_alter) over [`hook_entity_view_alter()`](http://api.drupal.org/api/search/7/hook_entity_view_alter) if only one entity type is expected.
- Prefer custom field formatters over custom alters when possible.
