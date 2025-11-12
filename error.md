# Error Solution

## 251112 settings
에러 메세지
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

에러: 용량 꽉참

해결: runpod의 "Pod Volume"에 저장하면됨
```bash
git clone https://huggingface.co/datalab-to/chandra /workspace/datalab-to/chandra
```
