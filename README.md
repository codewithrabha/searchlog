# searchlog
This PHP function logs the search keywords used on a WordPress website, along with the number of times each keyword has been searched and the IP addresses of the users who searched for those keywords. The function checks if the current query is a search query and then uses the WordPress database object ($wpdb) to query a custom table named 'wp_jet_cct_search_log'. If the search keyword already exists in the database, it updates the search count and logs the IP address of the user if it hasn't been already logged. If the search keyword doesn't exist, it inserts a new row into the table with the search keyword, search count, and the IP address of the user. The function is hooked to the pre_get_posts action in WordPress, which is called before the main query is executed, so that it can intercept and log any search queries.

1. Replace 'wp_jet_cct_search_log' with you CCT Database table.
2. Create 'search_keyword' (Custom filed) for your CCT.
3. Create 'ip_addresses' (Custom filed) for your CCT.
4. Create 'search_count' (Custom filed) for your CCT.
5. Change the OpenSSL Secret key as per your wish.

This code create logs of search keywords and IP addresses of users who search for those keywords on a website. The function is triggered when a user performs a search on the website and the pre_get_posts action is fired.

The search_keywords() function first checks if the current user is an administrator or if the current query is not the main query, and if either condition is met, it returns without doing anything. This is to ensure that the logging functionality is only executed for non-admin users and for the main search query.

If the current query is a search query, the function retrieves the searched keyword, converts it to lowercase, and checks if there is a record of the keyword in the wp_jet_cct_search_log table in the WordPress database. If a record is found, the search count is incremented by one, and the IP address of the current user is added to the list of IP addresses associated with the searched keyword.

If there is no record of the keyword in the wp_jet_cct_search_log table, a new record is inserted with a search count of one and the IP address of the current user is added to the list of IP addresses associated with the keyword.

The IP addresses are encrypted using the openssl_encrypt() function with the AES-256-CTR cipher and a secret key and IV that are hardcoded in the code. The serialize() function is used to convert the IP address array to a string before encryption, and the unserialize() function is used to convert it back to an array after decryption.

Overall, this php code provides a simple way to log search keywords and IP addresses on a WordPress website, which could be useful for tracking user behavior and improving search functionality. However, it should be noted that the use of a hardcoded key and IV for encryption is not secure and could be easily compromised by an attacker with access to the code.
