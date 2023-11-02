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

Wheels are built using GitHub Actions on Ubuntu 20.04, and repaired with:

```
auditwheel repair auto_gptq-0.5.0-cp310-cp310-linux_x86_64.whl \
    --plat manylinux_2_17_x86_64 \
    --exclude libtorch_python.so \
    --exclude libc10.so \
    --exclude libtorch_cpu.so \
    --exclude libcudart.so.12 \
    --exclude libcudart.so.12 \
    --exclude libc10_cuda.so \
    --exclude libtorch_cuda.so
```

and optionally for rocm: `--exclude libtorch_hip.so --exclude libamdhip64.so.5 --exclude libc10_hip.so`.

Maybe there is a better way.
