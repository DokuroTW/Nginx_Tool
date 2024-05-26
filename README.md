# Nginx_Tool
Nginx config黨

此設定檔包含了對資安基本的設定，透過ZAP攻擊驗證，但只有部分有效建議還是使用WAF

# server leaks version information via 'server' http Response header field  
    server_tokens off;
 # Strict-Transport-Security Header Not Set 
    add_header Strict-Transport-Security "max-age=31536000; includeSubDomains; preload" always;
 # Missing Anti-clickjacking Header
    add_header X-Frame-Options SAMEORIGIN; 
 # Content Security Policy (CSP) Header Not Set 
    add_header Content-Security-Policy "default-src 'self';" always;
 # x-conten-type-option header Missing
    add_header X-Content-Type-Options nosniff; 
 # Re-examine Cache-control Directives
    add_header Cache-Control "no-cache, no-store, must-revalidate";
 # XSS Protect(strong)  
    add_header X-XSS-Protection "1; mode=block";
 # CSRF Protect(strong)
    add_header Referrer-Policy "same-origin";
 # SQL injection(strong)
    client_max_body_size 1m;
 # HTTP Header Injection(strong)
    ignore_invalid_headers on;
 # Multiple X-Frame-Options Header Entries  
    proxy_hide_header X-Frame-Options;
 # Cookie Without Secure Flag && Cookie with SameSite Attribute None
    proxy_cookie_path / "/; secure; HttpOnly; SameSite=Strict";
 # Directory Traversal(strong)
    autoindex off;
