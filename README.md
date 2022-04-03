# qcloud-cos-deploy-action

此仓库的目的是帮助下载腾讯云COS工具[coscli](https://github.com/tencentyun/coscli)，并且生成对应的配置。

更多coscli文档请参考[腾讯云官方文档](https://cloud.tencent.com/document/product/436/63143)

### 使用方式：
``` yaml
jobs:
  test_job:
    runs-on: ubuntu-latest
    name: test coscli config
    steps:
      - uses: actions/checkout@v3
      - id: foo
        uses: wangchaoyi/qcloud-cos-deploy-action@main
        with:
          secret_id: ${{ secrets.QCLOUD_COS_SECRET_ID }}
          secret_key: ${{ secrets.QCLOUD_COS_SECRET_KEY }}
          token: ""
          buckets: ${{ secrets.QCLOUD_COS_BUCKETS }}
          region: ap-shanghai
      - run: coscli ls cos://${{ secrets.QCLOUD_COS_BUCKETS }}
        shell: bash
```