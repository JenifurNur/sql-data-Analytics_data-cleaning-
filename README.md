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
