#Linux配置

##文件权限

chmod -R 777 directory 给目录下所有文件给予所有权限

> chmod u+x file                　　　   给file的属主增加执行权限
> $ chmod 751 file                　　　   给file的属主分配读、写、执行(7)的权限，给file的所在组分配读、执行(5)的权限，给其他用户分配执行(1)的权限
> $ chmod u=rwx,g=rx,o=x file      上例的另一种形式
> $ chmod =r file                 　　　　为所有用户分配读权限
> $ chmod 444 file              　　　　 同上例
> $ chmod a-wx,a+r   file   　　 　   同上例
> $ chmod -R u+r directory       　   递归地给directory目录下所有文件和子目录的属主分配读的权限
> $ chmod 4755                          　　设置用ID，给属主分配读、写和执行权限，给组和其他用户分配读、执行的权限。
