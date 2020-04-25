# django3-cheat-sheet

## Model field reference

```python
from django.db import models
```

- Field options
  * null  
  * blank
  * choices
  * db_column
  * db_index
  * db_tablespace
  * default
  * editable
  * error_messages
  * help_text
  * primary_key
  * unique
  * unique_for_date
  * unique_for_month
  * unique_for_year
  * verbose_name
  * validators

- Fields types
  * AutoField
    ```python
    class AutoField(**options)
    ```
  * BigAutoField
    ```python
    class BigAutoField(**options)
    ```
  * BigIntegerField
  ```python
  class BigIntegerField(**options)
  ```
  * BinaryField
    ```python
    class BinaryField(max_length=None, **options)
    ```
  * BooleanField
    ```python
    class BooleanField(**options)
    ```
  * CharField
    ```python
    class CharField(max_length=None, **options)
    ```
  * DateField
    ```python
    class DateField(auto_now=False, auto_now_add=False, **options)
    ```
  * DateTimeField
    ```python
    class DateTimeField(auto_now=False, auto_now_add=False, **options)
    ```
  * DecimalField
    ```python
    class DecimalField(max_digits=None, decimal_places=None, **options)
    ```
  * DurationField
    ```python
    class DurationField(**options)
    ```
  * EmailField
  ```python
  class EmailField(max_length=254, **options)
  ```
  * FileField
    * FieldFile
  ```python
  class FileField(upload_to=None, max_length=100, **options)
  ```
  * FilePathField
  ```python
  class FilePathField(path=None, match=None, recursive=False, max_length=100, **options)
  ```
    * FilePathField.allow_files
    * FilePathField.allow_folders
  * FloatField
  ```python
  class FloatField(**options)
  ```
  * ImageField
  ```python
  class ImageField(upload_to=None, height_field=None, width_field=None, max_length=100, **options)
  ```
  * IntegerField
  ```python
  class IntegerField(**options)
  ```
  * GenericIPAddressField
  ```python
  class GenericIPAddressField(protocol=’both’, unpack_ipv4=False, **options)
  ```
  * NullBooleanField
  ```python
  class NullBooleanField(**options)
  ```
  * PositiveBigIntegerField
  ```python
  class PositiveBigIntegerField(**options)
  ```
  * PositiveIntegerField
  ```python
  class PositiveIntegerField(**options)
  ```
  * PositiveSmallIntegerField
  ```python
  class PositiveSmallIntegerField(**options)
  ```
  * SlugField
  ```python
  class SlugField(max_length=50, **options)
  ```
  This is a field intended to be used in URLs. A slug is a
  short label that contains only letters, numbers, underscores,
  or hyphens.
  * SmallAutoField
  ```python
  class SmallAutoField(**options)
  ```
  * SmallIntegerField
  ```python
  class SmallIntegerField(**options)
  ```
  * TextField
  ```python
  class TextField(**options)
  ```
  * TimeField
  ```python
  class TimeField(auto_now=False, auto_now_add=False, **options)
  ```
  * URLField
  ```python
  class URLField(max_length=200, **options)
  ```
  * UUIDField
  ```python
  class UUIDField(**options)
  ```

- Model Meta options
  * abstract
  * app_label
  * base_manager_name
  * db_table
    * Tablenames
  * db_tablespace
  * default_manager_name
  * default_related_name
  * get_latest_by
  * managed
  * order_with_respect_to
  * ordering
  * permissions
  * default_permissions
  * proxy
  * required_db_features
  * required_db_vendor
  * select_on_save
  * indexes
  * unique_together
  * index_together
  * constraints
  * verbose_name
  * verbose_name_plural
- Read-only Meta attributes
  * label
  * label_lower

- Relationship fields
  * ForeignKey
  ```python
  class ForeignKey(to, on_delete, **options)
  ```
    A many-to-one relationship. Requires two positional arguments:
    the class to which the model is related and the on_delete option.

    To create a recursive relationship – an object that has a many-to-one
    relationship with itself – use models.ForeignKey('self', on_delete=models.CASCADE)
      * ForeignKey on_delete arguments
        * CASCADE
          > Cascade deletes. Django emulates the behavior of the SQL constraint ON DELETE CASCADE and also deletes the object containing the ForeignKey.
          >
          > Model.delete() isn’t called on related models, but the pre_delete and post_delete signals are sent for all deleted objects.

        * PROTECT
          > Prevent deletion of the referenced object by raising ProtectedError, a subclass of django.db.IntegrityError.

        * SET_NULL
          > Set the ForeignKey null; this is only possible if null is   True.

        * SET_DEFAULT
          > Set the **ForeignKey** to its default value; a default for the **ForeignKey** must be set.

        * SET()
          > Set the **ForeignKey** to the value passed to SET(), or if a callable is passed in, the result of calling it. In most cases, passing a       callable will be necessary to avoid executing queries at the time your models.py is imported:

## Form fields

  * Field
  *

## Authentication

- Authentication class

```python
from django.contrib.auth.models import User

```
- Class Fields
  * username
  * first_name
  * last_name
  * email
  * password
  * groups
  * user_permissions
  * is_staff
  * is_active
  * is_superuser
  * last_login
  * date_joined

- Class Attributes
  * is_authenticated
  * is_anonymous

- Class Methods
  * get_username()
  * get_full_name()
  * get_short_name()
  * set_password()
  * check_password()
  * set_unusable_password()
  * has_usable_password()
  * get_user_permissions(obj=None)
  * get_group_permissions(obj=None)
  * get_all_permissions(obj=None)
  * has_perm(perm, obj=None)
  * has_perms(perm_list, obj=None)
  * has_module_perms(package_name)
  * email_user(subject, message, form_email=None, )

- manage.py commands
  * check
  * compilemessages
  * createcachetable
  * dbshell
  * diffsettings
  * dumpdata
  * flush
  * inspectdb
  * loaddata
  * makemessages
  * makemigrations
  * migrate
  * runserver
  * sendtestemail
  * shell
  * showmigrations
  * sqlflush
  * sqlmigrate
  * sqlsequencereset
  * squashmigrations
  * startapp
  * startproject
  * test
  * testserver
