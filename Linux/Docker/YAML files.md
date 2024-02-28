Tabs and spaces are very important

https://docs.docker.com/compose/reference/

```yaml
version: "3"
services:

	volumes:
		- ./name : /user/share/location
	or
	volumes: 
		-db_vol: /var/lib/mysql

volumes:
	db_vol
```

To add volume on the local machine or folder
```yaml
./[FOLDER NAME]
```





Docker Compose has Environment Variable files. its a .env file - this is for like passwords and what not. 