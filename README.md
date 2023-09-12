            const {
              companyJobPost,
            } = require("../../models/company.model/Jobpost.company..model");
            
            module.exports.allJob = async (req, res, next) => {
              try {
                if (req.query.page) {
                  const { page = 1, limit = 10 } = req.query;
            
                  const skip = (page - 1) * parseInt(limit);
            
                  const allJob = await companyJobPost
                    .find({})
                    .skip(skip)
                    .limit(parseInt(limit));
            
                  const totalJob = await companyJobPost.countDocuments();
            
                  res.send({
                    message: "success",
                    totalJob: totalJob,
                    value: allJob,
                  });
                } else {
                  const allJob = await companyJobPost.find({});
                  const totalJob = await companyJobPost.countDocuments();
                  res.send({
                    message: "success",
                    totalJob: totalJob,
                    value: allJob,
                  });
                }
              } catch (error) {
                res.send({
                  message: error.message,
                  error: error,
                });
              }
            };
