## HUGO BLOG

## 启动
docker run --rm -it -v $PWD:/src -p 1313:1313 -u hugo jguyomard/hugo-builder hugo server -w --bind=0.0.0.0

## 编译
docker run --rm -it -v $PWD:/src -u hugo jguyomard/hugo-builder hugo