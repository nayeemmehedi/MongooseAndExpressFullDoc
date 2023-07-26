### router doc

        const express = require("express");
        const {
          Home,
          HomePost,
          HomePatch,
          HomeDelete,
          HomeBulkupdateAll,
          HomeBulkupdateDiffernt,
        } = require("../controller/home.controller");
        
        const routesHome = express.Router();
        
        routesHome.route("/").get(Home).post(HomePost);
        
        routesHome.patch("/bulkupdateAll", HomeBulkupdateAll);
        routesHome.patch("/bulkupdateDiffernt", HomeBulkupdateDiffernt);
        
        routesHome.patch("/:id", HomePatch);
        routesHome.delete("/:id", HomeDelete);
        
        module.exports = routesHome;
