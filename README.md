# SFDC_Utility

Questions :
  Q1. What is the difference between <template if:true> and <div if:true>
  Answer 1. :

  Q2. Zombie Jobs in Salesforce.
  Answer 1. To Abort Job we need to login to workbench and set the api version to 31 to lower and try to execute following script 
          for(AsyncApexJob obj : [Select Id from AsyncApexJob]){
              System.abortJob(obj.Id);
          }
          Here the field CronTriggerId field was not present in the past version of salesforce i.e. lower than v31.0
