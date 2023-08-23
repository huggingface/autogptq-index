Hosted wheels for AutoGPTQ for [cuda build](https://github.com/PanQiWei/AutoGPTQ/actions/workflows/build_wheels_cuda.yml) and [rocm build](https://github.com/PanQiWei/AutoGPTQ/actions/workflows/build_wheels_rocm.yml).

To rebuild the index:
```
cd whl
find . -type d -print -exec sh -c 'tree "$0" \
    -H "." \
    -L 1 \
    --noreport \
    --dirsfirst \
    --charset utf-8 \
    -I "index.html" \
    --ignore-case \
    --timefmt "%d-%b-%Y %H:%M" \
    -s \
    -D \
    -o "$0/index.html"' {} \;
```
