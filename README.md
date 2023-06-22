# django-manage-permissions
manage django user permissions

### 0-from django.contrib.auth.models import PermissionsMixin

### 1-inherite User from PermissionsMixin.

> note : we must initialize is_superuseer variable with True for our admin user, we don't need has_perm and has_perms methods in our custom user model anymore.
--don't unregister groups in user model

### 2-go to admin.py > fieldsets > permissions add 'groups','user_permissions','last_login','is_superuser' to tuple.

### 3-filter_horizontal = ('groups','user_permissions')

### 4-readonly_fields = 'last_login'

### 5- add some groups to manage users

### 6- add users while registering to different groups 

### 7- go to your custom user manager and add following code to " createsuperuser "  function :
> user.is_superuser = True

## ------ NOTES ------


#### note :>> 'admin' means user can enter adminpanel & 'super_user' can access all control in admin panel


#### list users of a group :
```
users = User.objects.filter(groups__name = 'name of group')
```


#### add user to a group ::
```
user = request.user
pro_users = Group.objects.get('pro_users')
pro_users.user_set.add(user)
```
