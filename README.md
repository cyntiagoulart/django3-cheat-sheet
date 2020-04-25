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
    Boolean. Designates whether this user can access the admin site.
  * is_active
    Boolean. Designates whether this user account should be considered active.
  * is_superuser
    Boolean. Designates that this user has all permissions without explicitly assigning them.
  * last_login
    A datetime of the user’s last login.
  * date_joined
    A datetime designating when the account was created. Is set to the current date/time by default when the account is created.

- Class Attributes
  * is_authenticated
    Read-only attribute which is always True (as opposed to AnonymousUser.is_authenticated which is always False). This is a way to tell if the user has been authenticated. This does not imply any permissions and doesn’t check if the user is active or has a valid session.
  * is_anonymous
    Read-only attribute which is always False. This is a way of differentiating User and AnonymousUser objects. Generally, you should prefer using is_authenticated to this attribute.

- Class Methods
- class models.User

  * get_username()
    Returns the username for the user. Since the User model can be swapped out, you should use this method instead of referencing the username attribute directly.
  * get_full_name()
    Returns the first_name plus the last_name, with a space in between.
  * get_short_name()
    Returns the first_name.
  * set_password(raw_password)
    Sets the user’s password to the given raw string, taking care of the password hashing. Doesn’t save the User object.
  * check_password(raw_password)
    Returns True if the given raw string is the correct password for the user. (This takes care of the password hashing in making the comparison.)
  * set_unusable_password()
  * has_usable_password()
  - New in Django3.0
  * get_user_permissions(obj=None)
    Returns a set of permission strings that the user has directly.
    If obj is passed in, only returns the user permissions for this specific object
  * get_group_permissions(obj=None)
    Returns a set of permission strings that the user has, through their groups.
    If obj is passed in, only returns the group permissions for this specific object.
  * get_all_permissions(obj=None)
    Returns a set of permission strings that the user has, both through group and user permissions.
    If obj is passed in, only returns the permissions for this specific object
  * has_perm(perm, obj=None)
    Returns True if the user has the specified permission, where perm is in the format "<app label>.<permission codename>".
    If the user is inactive, this method will always return False. For an active superuser, this method will always return True
  * has_perms(perm_list, obj=None)
    Returns True if the user has each of the specified permissions, where each perm is in the format "<app label>.<permission codename>". If the user is inactive, this method will always return False. For an active superuser, this method will always return True.
  * has_module_perms(package_name)
    Returns True if the user has any permissions in the given package (the Django app label). If the user is inactive, this method will always return False. For an active superuser, this method will always return True.
  * email_user(subject, message, from_email=None, **kwargs)
    Sends an email to the user. If from_email is None, Django uses the DEFAULT_FROM_EMAIL. Any `**kwargs` are passed to the underlying send_mail() call.

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
