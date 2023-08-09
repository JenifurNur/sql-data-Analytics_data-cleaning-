


# sql-data-Analytics_data-cleaning-
SELECT
  purchase_price

FROM
  customer_data.customer_purchase

ORDER BY
  purchase_price DESC

#for typecasting to recongnize or reorganize the data, or to recongnize the number as float rather than string...###
#CAST function to allow SQL to recognize the purchase_price column as floats instead of text strings.#
SELECT
  CAST(purchase_price AS FLOAT64)

FROM
  customer_data.customer_purchase

ORDER BY
  CAST(purchase_price AS FLOAT64) DESC
#-------------#

#to filter for purchases that occurred in December only#
SELECT
  date,
  purchase_price

FROM
  customer_data.customer_purchase

WHERE
  date between '2020-12-01' AND '2020-12-31'
#---------------------------------------------------------------#

#CAST() function tell SQL to convert the date field into the date data type so we see just the day and not the time.#
SELECT
  CAST(date AS date) AS date_only,
  purchase_price

FROM
  customer_data.customer_purchase

WHERE
  date between '2020-12-01' AND '2020-12-31'
#-----------------------------------------------------#

#***-------------------------CONCAT lets you add strings together to create new text strings that can be used as unique keys.--------------*#
# CONCAT() function here to get that unique key of product and color. can count how many times each couch was purchased and figure out if customers preferred one color over the others #

SELECT
  CONCAT(product_code, product_color) AS new_product_code

FROM
customer_data.customer_purchase

WHERE
  product= 'couch'

  #----------------------------------------------------#
  #  COALESCE can be used to return non-null values in a list.#
  #But if the product name doesn't exist, we can tell SQL to give us the product_code instead. That is where the COALESCE function comes into play. to use the product_name column to understand what kind of product was sold.  if names aren't available, then give us the product code.  type "COALESCE." then we tell SQL which column to check first, product, and which column to check second if the first column is null, product_code. We'll name this new field as product_info.  #

SELECT
  COALESCE(product, product_code) AS product_info

FROM
  customer_data.customer_purchase
  #----------------------------------------------------------------#
