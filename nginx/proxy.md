
### Prxy buffer

- https://www.digitalocean.com/community/tutorials/understanding-nginx-http-proxying-load-balancing-buffering-and-caching
- 前提：ブラウザ・Nginx間とNginx・アップストリーム間の2つの速度の異なるコネクションがある
- アップストリームのレスポンスをNginxにバッファすることで、アップストリームへのコネクションを速く閉じられる
- 関連ディレクティブ
  - proxy_buffering：バッファのオンオフ
  - proxy_buffers：バッファ数とバッファサイズ
  - proxy_buffer_size：レスポンスヘッダ用のバッファ（デフォルトはproxy_buffersと同じ）
  - proxy_busy_buffers_size：client-readyとなるバッファ数？
  - proxy_max_temp_file_size：バッファに書き込むにはデカすぎるレスポンス用の一時ファイル
  - proxy_temp_file_write_size：一時ファイルに書き込むサイズ
  - proxy_temp_path：一時ファイルの場所
 
