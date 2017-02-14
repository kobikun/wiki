# ChatBot
* What is chatbot?
 * 사용자가 웹사이트나 앱을 따로 실행하지 않아도, 대화를 통해 정보를 얻을 수 있는 서비스
* Why Chatbot?

# Data for Chatbot

* [Ubuntu set](https://github.com/rkadlec/ubuntu-ranking-dataset-creator) (English)
* [Definition of Question Classes](http://cogcomp.cs.illinois.edu/Data/QA/QC/definition.html) (English)
* [Experimental Data for Question Classification](http://cogcomp.cs.illinois.edu/Data/QA/QC/) (English)

* [ConceptNet](https://github.com/silentrob/conceptnet) 

* [RiveScript : Simple scripting language for chatbot](https://www.rivescript.com/)
 * [RiveScript for Python](https://github.com/aichaos/rivescript-python)

# Papers

### [A Neural Convesational Model](https://arxiv.org/pdf/1506.05869v3.pdf)
* Oriol Vinyals(Google), Quoc V.Le (Google)
* using Seq2Seq
* Datasets
 * IT Helpdesk Troubleshooting : 30M tokens(training), 3M tokens(validation)
 * OpenSubtitles : 62M sentences(923M token, training) 26M sentences(395M tokens)
* `CleverBot`(규칙기반)과 성능 비교
* 200개 질문 셋을 이용
* IT Helpdesk
 * LSTM : 단일 레이어 / 1024 memory cells
 * Vocabulary size : 20K
 * special tokens : taking & actor
* OpenSubtitles
 * LSTM : 2레이어, AdaGrad / 4096 memory cell
 * Vocabulary size : 100K word

# Articles

* [Creating a chat bot](https://medium.freecodecamp.com/creating-a-chat-bot-42861e6a2acd#.mmktpfirv) (English)
* [OSS 챗봇이란](http://www.oss.kr/oss_repository14/655130) (Korean)

* [대화형 챗봇 설계의 과제](https://gist.github.com/haje01/7fc9d1b1fc1b6c8c9b7918abf5407a86) (Korean)

* [혼자 힘으로 한국어 챗봇 개발하기](http://exagen.tistory.com/notice/63) (Korean)
 * Chatscript을 이용하여 챗봇을 만든 경험에 대한 글.
