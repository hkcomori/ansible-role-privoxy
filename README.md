# ansible-role-privoxy

[![Build Status](https://travis-ci.org/tkimball83/ansible-role-privoxy.svg?branch=master)](https://travis-ci.org/tkimball83/ansible-role-privoxy)

macOS - A non-caching web proxy

## Requirements

This role requires homebrew to be installed.

## Role Variables

Available variables are listed below, along with default values:

    privoxy_accept_intercepted_requests: False
    privoxy_actionsfiles:
      - match-all.action
      - default.action
      - user.action
    privoxy_allow_cgi_request_crunching: False
    privoxy_buffer_limit: 4096
    privoxy_compression_level: 1
    privoxy_confdir: /usr/local/etc/privoxy
    privoxy_connection_sharing: False
    privoxy_debug:
      - 0
    privoxy_default_server_timeout: 60
    privoxy_enable_compression: False
    privoxy_enable_edit_actions: False
    privoxy_enable_remote_toggle: False
    privoxy_enable_remote_http_toggle: False
    privoxy_enable_proxy_authentication_forwarding: False
    privoxy_enforce_blocks: False
    privoxy_filterfiles:
      - default.filter
      - user.filter
    privoxy_forwarded_connect_retries: '0'
    privoxy_handle_as_empty_doc_returns_ok: False
    privoxy_hostname: "{{ inventory_hostname }}"
    privoxy_keep_alive_timeout: 5
    privoxy_listen_address: '127.0.0.1:8118'
    privoxy_logdir: /usr/local/var/log/privoxy
    privoxy_logfile: logfile
    privoxy_max_client_connections: 128
    privoxy_single_threaded: False
    privoxy_split_large_forms: False
    privoxy_socket_timeout: 300
    privoxy_toggle: True
    privoxy_tolerate_pipelining: True
    privoxy_user_manual: /usr/local/share/doc/privoxy/user-manual

Additional variables not defined by default:

    privoxy_admin_address: privoxy-admin@example.com
    privoxy_client_header_order:
      - Host
      - Accept
      - Cookie
      - Content-Length
      - Content-Type
    privoxy_forward:
      - target_pattern: /
        http_parent: parent-proxy.example.org:8080
    privoxy_forward_socks4:
      - target_pattern: /
        socks_proxy: socks-gw.example.com:1080
        http_parent: '.'
    privoxy_forward_socks4a:
      - target_pattern: /
        socks_proxy: socks-gw.example.com:1080
        http_parent: www-cache.isp.example.net:8080
    privoxy_forward_socks5:
      - target_pattern: /
        socks_proxy: socks-gw.example.com:1080
        http_parent: www-cache.isp.example.net:8080
    privoxy_forward_socks5t:
      - target_pattern: /
        socks_proxy: 127.0.0.1:9050
        http_parent: '.'
    privoxy_permit_access:
      - src_addr: www.privoxy.org/24
        dst_addr: www.example.com/32
    privoxy_proxy_info_url: http://www.example.com/proxy-service.html
    privoxy_templdir: '.'
    privoxy_temporary_directory: '.'
    privoxy_trustfile: trust
    privoxy_trust_info_url:
      - http://www.example.com/why_we_block.html
      - http://www.example.com/what_we_allow.html
    
## Dependencies

None

## Example Playbook

    - hosts: localhost
      connection: local
      roles:
        - role: tkimball83.privoxy
          privoxy_admin_address: tkimball@linuxhq.org
          privoxy_forward_socks5t:
            - target_pattern: /
              socks_proxy: 127.0.0.1:9050
              http_parent: '.'

## License

GPLv3

## Author Information

This role was created by [Taylor Kimball](http://www.linuxhq.org).
