# Hive-Sql_Code_Example

SELECT
 if(YEAR(CURDATE())=YEAR(DeliveryDay)
  ,if(MONTH(CURDATE())-MONTH(DeliveryDay) >= 2
    ,CONCAT(YEAR(DeliveryDay),"-",MONTH(DeliveryDay),"-01")
    ,DeliveryDay)
  ,if(MONTH(CURDATE())+12-MONTH(DeliveryDay) >=2
      ,CONCAT(YEAR(DeliveryDay),"-",MONTH(DeliveryDay),"-01")
      ,DeliveryDay)) as increment_day
  , IF(tempestindicator = 1, audienceownerusername, NULL) AS audienceownerusername
  , IF(tempestindicator = 1, partnerId, NULL) AS partnerId
  , IF(tempestindicator = 1, partnername, NULL) AS partnername
  , IF(tempestindicator = 1, businessrelationshipname, NULL) AS businessrelationshipname
  , IF(tempestindicator = 1, adintegrationid, NULL) AS adintegrationid
  , IF(tempestindicator = 1, adintegrationname, NULL) AS adintegrationname
  , opportunitylineitemfunctionalsalespriceamount
  , product
  , billingmetriccode
  , tempestindicator
  , country
  , audiencetargetcodelist
  , dimensioncode
  , devicecontextcode
  --Need verification if rtbrevenue from beacons is accurate
  , sum(rtbrevenue) as rtbrevenue
  , sum(payout) as payout
  , sum(exchangepricepaid) as exchangepricepaid
  , sum(avail) as avail
  , max(maximpression) as maximpression
  , max(maxclick) as maxclick
  , sum(adserverimpressioncount) as adserverimpressioncount
  , sum(adserverclickcount) as adserverclickcount
  , sum(sessioncount) as sessioncount
  , SUM(impressioncount) AS impressioncount
  , SUM(viewablecount) AS viewablecount
  , SUM(engagementcount) AS engagementcount
  , SUM(clicktositetotalcount) clicktositetotalcount
FROM VDAT_5942
 where increment_day >= DATE_SUB(CURDATE(), 3)
GROUP BY
if(YEAR(CURDATE())=YEAR(DeliveryDay)
  ,if(MONTH(CURDATE())-MONTH(DeliveryDay) >= 2
    ,CONCAT(YEAR(DeliveryDay),"-",MONTH(DeliveryDay),"-01")
    ,DeliveryDay)
  ,if(MONTH(CURDATE())+12-MONTH(DeliveryDay) >=2
      ,CONCAT(YEAR(DeliveryDay),"-",MONTH(DeliveryDay),"-01")
      ,DeliveryDay))
  , IF(tempestindicator = 1, audienceownerusername, NULL)
  , IF(tempestindicator = 1, partnerId, NULL)
  , IF(tempestindicator = 1, partnername, NULL)
  , IF(tempestindicator = 1, businessrelationshipname, NULL)
  , IF(tempestindicator = 1, adintegrationid, NULL)
  , IF(tempestindicator = 1, adintegrationname, NULL)
  , opportunitylineitemfunctionalsalespriceamount
  , product
  , billingmetriccode
  , tempestindicator
  , country
  , audiencetargetcodelist
  , dimensioncode
  , devicecontextcode
5563 Pulse Tempe
