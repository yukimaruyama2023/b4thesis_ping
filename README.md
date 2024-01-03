# 概要
ping において受信したデータを csv ファイルに吐き出すように．ping のソースコードを改変した．
具体的には，サーバが icmp パケットにメトリクスを載せ，クライアントはそれを受信するが，
- 受信時刻
- 要した時間
- メトリクス
を csv ファイルに吐き出すように改変した．

# 関数の流れ
main()->ping_run()->main_loop()->pinger()->send_probe()->sendto()　(ここでメッセージ送信)
                               ->parse_reply()(ping4_parse_replyに変換)->ip->ttl　(ここで，ttlがわかる)
                                                                      ->gather_statictics()->cp (ここで，メトリクスへアクセスできる．)
