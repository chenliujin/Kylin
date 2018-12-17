# Query

# CUBE
* List cubes
* Build cube

---

# kylin/api/query
* METHOD: `POST`
* Param:
  - sql
  - offset
  - limit
  - acceptPartial
  - project


# kylin/api/cubes/{cube_name}/rebuild

* METHOD: `PUT`
* Param:
  - startTime: `utc timestamp`, utc time * 1000
  - endTime: `utc timestamp`
  - buildType: BUILD/MERGE/REFRESH

```
PUT http://localhost:7070/kylin/api/cubes/test_kylin_cube_with_slr/rebuild

Authorization:Basic xxxxJD124xxxGFxxxSDF
Content-Type: application/json;charset=UTF-8

{
    "startTime": 0,
    "endTime": 1388563200000,
    "buildType": "BUILD"
}
```

# 参考文献
* [RESTful API](http://kylin.apache.org/docs/howto/howto_use_restapi.html#build-cube)
* [Build Cube with API](http://kylin.apache.org/docs/howto/howto_build_cube_with_restapi.html)
