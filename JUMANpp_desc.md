# JUMANpp
* JUMAN(기존 규칙 기반 일본어 형태소 분석기)를 기반으로 deep learning 기술을 적용한 형태소 분석기
* site : http://nlp.ist.i.kyoto-u.ac.jp/index.php?JUMAN++

* RNN 언어 모델 학습 : 웹코퍼스 1000만
* 학습/평가 데이터 : NEWS/WEB (교토 코퍼스)

* 사전 : JUMA에서의 사전 이용

## 기본 사전
* 대표표기 (unidic의 어휘소?) : 대표표기/lemma/후리가나(카타)
* 1음절에 대해서는 음/훈 구별 
* 가능동사의 경우 원형
* 존경/겸양 동사의 경우 -> 원형
 *  おっしゃる → 尊敬動詞：言う
* 자동사/타동사 : 대응관계
 * `壊れる → 自他動詞：他:壊す`, `壊す → 自他動詞:自:壊れる`
* 수수동사의 대응관계
* 반의
 * 増える → 反義:動詞:減る
 * 大きい → 反義:動詞:小さい
* 파생
 * 大人びる → 名詞派生:大人
 * 高める → 形容詞派生:高い

## links 
* https://drive.google.com/file/d/1DVnrsWw4skRgC8jU6_RkeofOQEHFwctc/view
* https://qiita.com/riverwell/items/438e88427363511e9f28


# library
* fastrnn ( https://github.com/yandex/faster-rnnlm ) : JUMANpp에서 사용한 language model tool.

