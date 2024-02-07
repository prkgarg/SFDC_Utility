# SFDC_Utility

Questions :
  Q1. What is the difference between <template if:true> and <div if:true>
  Answer 1. :

  Q2. Zombie Jobs in Salesforce.<br/>
  Answer 2. To Abort Job we need to login to workbench and set the api version to 31 to lower and try to execute following script 
          for(AsyncApexJob obj : [Select Id from AsyncApexJob]){
              System.abortJob(obj.Id);
          }
          Here the field CronTriggerId field was not present in the past version of salesforce i.e. lower than v31.0
  
  <br/><br/>
  Q3. In the Classic Email Template we use the "{!Community_url}" variable in the case when we want to pass the reset url or login url for the Community user. But we can't use this variable in the VF Email Template i.e. the VF component.<br/>
  ** Answer 3. : ** Solution for this situation is to use the "{!$Network.NetworkUrlForUserEmails}" in the VF html code in the place of "{!Community_url}" and also make sure that the email template header tag i.e. "<messaging:emailTemplate>" should have the following properties and values: <br/>
  <ul>
    <li>recipientType="User"</li>
    <li>relatedToType="Community"</li>
    <li>renderUsingSystemContextWithoutSharing="true"</li>
  </ul>  
  Following are the reference links regarding this solution :<br/>
    > Link 1 : https://salesforce.stackexchange.com/questions/258517/how-to-get-community-url-in-a-visualforce-email-template<br/>
    > Link 2 : https://salesforce.stackexchange.com/questions/367391/community-welcome-email-visualforce-is-not-sent<br/>
    > Link 3 : https://help.salesforce.com/s/articleView?id=sf.email_templates_vf_modify_for_guest.htm&type=5<br/>

<br/><br/><br/>

  Q4. How do we read a Encrypted field value in apex class.<br/><br/>
  Answer 4.     PageReference ref = new PageReference('/apex/mypage');<br/>
                ref.getParameters().put('param', paymentMethod.Credit_Card_Number__c);<br/>
                String decryptedFieldValue = ref.getParameters().get('param');<br/>
                //or if you want to get value for example in getter method<br/>
                //String decryptedFieldValue = ApexPages.currentPage().getParameters().get('param');<br/>
          Now you can use "decryptedFieldValue" variable which contains the information. <br/>
