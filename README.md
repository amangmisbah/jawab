#disini saya menggunakan pentaho untuk extract data dan load data
![image](https://github.com/amangmisbah/jawab/assets/72803669/62e663ac-2ed6-4427-b310-6cbbb316218b)
ini untuk extract data csv dan json lalu di load ke mysql server
SELECT c.first_name, c.last_name, SUM(td.item_quantity * td.item_price) AS total_spent,
       GROUP_CONCAT(DISTINCT p.product_name) AS products_bought,
       GROUP_CONCAT(DISTINCT s.store_name) AS stores_visited
FROM transaction_data td
JOIN customer c ON td.customer_fk = c.customer_id
JOIN product p ON td.produk_fk = p.product_id
JOIN store s ON td.store_fk = s.store_id
GROUP BY c.customer_id
ORDER BY total_spent DESC
LIMIT 5;
