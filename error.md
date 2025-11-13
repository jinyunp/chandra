# Error Solution

## 251112 settings

1. Download huggingface model: datalab-to/chandra
```bash
# Update basics
sudo apt-get update -y

# Git + Git LFS
sudo apt-get install -y git git-lfs
git lfs install

# Install Git-Xet (HF’s official script)
curl --proto '=https' --tlsv1.2 -sSf \
  https://raw.githubusercontent.com/huggingface/xet-core/refs/heads/main/git_xet/install.sh | sh

# sanity checks
git --version
git lfs version
git xet --version

#download from hf
git clone https://huggingface.co/datalab-to/chandra /workspace/datalab-to/chandra
```

### 에러
1. 에러: safetensor가 제대로된 파일이 아님
```bash
safetensors_rust.SafetensorError: Error while deserializing header: header too large
```
파일 크기 확인
```bash
ls -lh ./datalab-to/chandra/*safetensors
```
해결: git xet가 전역 설정에 필터가 install되지 않음
```bash
git xet install --system
```
이후 다시 clone 시도

2. 에러: 용량 꽉참

해결: runpod의 "Pod Volume"에 저장하면됨
```bash
git clone https://huggingface.co/datalab-to/chandra /workspace/datalab-to/chandra
```
