"use strict";
const Generator = require("yeoman-generator");
const database = require('./database')
module.exports = class extends Generator {


  constructor(args, opts) {
    super(args, opts);
    this.configOptions = this.options.configOptions || {};
    Object.assign(this.configOptions, this.config.getAll());
  }

 /* get prompting() {
    return prompts.prompting;
  }*/

  configuring() {

    let buildConfig = this.configOptions.buildConfig;
    let databaseType ;
    let host;
    let databaseName;
    let username;
    let password;
    this.config.set("database", 'exist')
    for(let feature of this.config.get("features")){
      if(feature.type === 'database'){
        databaseType = feature.databaseType
        host = feature.host
        databaseName = feature.databaseName
        username = feature.username
        password = feature.password
      }
    }



    if (buildConfig.frameWork == 'springboot') {
      if (databaseType == 'mysql') {
        this.config.set(this.config.get("prop")["database"] = {
          url: database.mysql_url + host + '/' + databaseName,
          driver: database.mysql_driver,
          jpa: database.mysql_jpa,
          username: username,
          password: password,
          databaseType : databaseType
        })

        this.config.set(this.config.get("dependencies").push({
          groupId: database.mysql_groupId,
          artifactId: database.mysql_artifactId
        })
        )
      } else if (databaseType == 'oracle') {
        this.config.set(this.config.get("prop")["database"] = {
          url: database.oracle_url,
          driver: database.oracle_driver,
          jpa: database.oracle_jpa,
          username: username,
          password: password,
          databaseType : databaseType
        })

        this.config.set(this.config.get("dependencies").push({
          groupId: database.oracle_groupId,
          artifactId: database.oracle_artifactId
        }))
      }
    } else {
      if (databaseType == 'mysql') {
        this.config.set(this.config.get("prop")["database"] = {
          url: database.mysql_url + host + '/' + databaseName,
          driver: database.mysql_driver,
          jpa: database.mysql_jpa,
          username: username,
          password: password,
          databaseType : databaseType
        })

        this.config.set(this.config.get("dependencies").push({
          groupId: database.quarkus_global_groupId,
          artifactId: database.quarkus_mysql
        })
        )
      }else if (databaseType == 'oracle') {
        this.config.set(this.config.get("prop")["database"] = {
          url: database.oracle_url,
          driver: database.oracle_driver,
          jpa: database.oracle_jpa,
          username: username,
          password: password,
          databaseType : databaseType
        })

        this.config.set(this.config.get("dependencies").push({
          groupId: database.oracle_groupId,
          artifactId: database.oracle_artifactId
        }))
      }
    }

  }


}


