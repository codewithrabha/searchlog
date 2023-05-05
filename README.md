# searchlog
This PHP function logs the search keywords used on a WordPress website, along with the number of times each keyword has been searched and the IP addresses of the users who searched for those keywords. The function checks if the current query is a search query and then uses the WordPress database object ($wpdb) to query a custom table named 'wp_jet_cct_search_log'. If the search keyword already exists in the database, it updates the search count and logs the IP address of the user if it hasn't been already logged. If the search keyword doesn't exist, it inserts a new row into the table with the search keyword, search count, and the IP address of the user. The function is hooked to the pre_get_posts action in WordPress, which is called before the main query is executed, so that it can intercept and log any search queries.

1. Replace 'wp_jet_cct_search_log' with you CCT Database table.
2. Create 'search_keyword' (Custom filed) for your CCT.
3. Create 'ip_addresses' (Custom filed) for your CCT.
4. Create 'search_count' (Custom filed) for your CCT.
5. Change the OpenSSL Secret key as per your wish.
