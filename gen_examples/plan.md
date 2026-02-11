План курса: «Информационный поиск и обработка текстов на естественном языке»

Тема 1. Классические методы NLP и информационного поиска
1.1 Формальные языки и грамматики

Иерархия Хомского: регулярные, контекстно-свободные (CFG), контекстно-зависимые грамматики
Вероятностные грамматики (PCFG), CYK-алгоритм разбора
Зависимостный и составляющий синтаксический анализ (dependency/constituency parsing)
Морфологический анализ: стемминг (Портер), лемматизация, POS-теггинг (HMM, Viterbi)

1.2 Статистический информационный поиск

Модель «мешок слов» (Bag of Words), инвертированный индекс
TF-IDF: формулировка, варианты нормализации, интерпретация
BM25 (Okapi BM25) как улучшение TF-IDF
Векторная модель пространства (VSM), косинусное сходство
Булевский и вероятностный поиск (Robertson-Sparck Jones)

1.3 Классические задачи и алгоритмы

Named Entity Recognition (NER) на правилах и CRF
Классификация текстов: Naïve Bayes, логистическая регрессия, SVM
Латентно-семантический анализ (LSA / SVD)
Латентное размещение Дирихле (LDA) — тематическое моделирование
Оценка качества IR: Precision@K, Recall, MAP, nDCG


Тема 2. N-граммные языковые модели и нейронные основы
2.1 N-граммные модели

Вероятностная цепочка Маркова, биграммы, триграммы
Сглаживание: Лаплас, Kneser-Ney, Good-Turing
Перплексия как метрика языковой модели

2.2 Нейронные сети, обратное распространение ошибки и эмбеддинги

Многослойный перцептрон (MLP), функции активации
Backpropagation: вычислительный граф, цепное правило
Word2Vec (CBOW, Skip-gram), GloVe, FastText
Геометрия векторного пространства: аналогии, кластеризация, bias в эмбеддингах

2.3 Функции потерь

Cross-Entropy Loss, связь с перплексией
Label smoothing, focal loss для несбалансированных классов


📄 Ключевые работы: Bengio et al. (2003) «A Neural Probabilistic Language Model»; Mikolov et al. (2013) Word2Vec


Тема 3. Рекуррентные нейронные сети (RNN)
3.1 Архитектура RNN и проблемы обучения

Развёртывание сети во времени (BPTT)
Проблемы взрывающихся и исчезающих градиентов
Gradient clipping, инициализация весов, layer normalization

3.2 LSTM и GRU

Ячейка LSTM: gate-механизмы (forget, input, output)
GRU как упрощённая альтернатива
Сравнительный анализ способности удерживать долгосрочные зависимости

3.3 Расширения RNN

Bidirectional RNN (ELMo как языковая модель)
Stacked (multi-layer) RNN
Dropout в рекуррентных сетях (Zoneout, variational dropout)

3.4 Seq2Seq и машинный перевод

Архитектура encoder–decoder на RNN
Механизм внимания Bahdanau (additive attention)
Механизм внимания Luong (multiplicative attention)
Teacher forcing и exposure bias


📄 Ключевые работы: Hochreiter & Schmidhuber (1997) LSTM; Sutskever et al. (2014) Seq2Seq; Bahdanau et al. (2015) Attention


Тема 4. Архитектура Transformer
4.1 Self-Attention в деталях

Query, Key, Value: матричная формулировка, scaled dot-product attention
Почему масштабирование на √d_k важно
Multi-head attention: параллельные подпространства внимания
Positional encoding: синусоидальный и обучаемый варианты
Сложность O(n²) и методы её снижения: Longformer, BigBird, FlashAttention

4.2 Полная архитектура Transformer

Encoder: стек слоёв, Add & Norm, Feed-Forward сеть
Decoder: masked self-attention, cross-attention
Pre-norm vs. Post-norm: влияние на стабильность обучения

4.3 Сценарии использования Encoder и Decoder

Encoder-only (BERT): классификация, NER, span extraction
Decoder-only (GPT): авторегрессионная генерация
Encoder-Decoder (T5, BART): перевод, резюмирование, seq2seq задачи


📄 Ключевые работы: Vaswani et al. (2017) «Attention Is All You Need»; Devlin et al. (2019) BERT; Radford et al. GPT-2/3


Тема 5. Предобучение и тонкая настройка
5.1 Парадигма pre-train → fine-tune

Цели предобучения: MLM, CLM, NSP, span corruption (T5)
Масштабирование: законы масштабирования Chinchilla (Hoffmann et al., 2022)
Adapter layers, prefix tuning, prompt tuning

5.2 Parameter-Efficient Fine-Tuning (PEFT)

LoRA (Low-Rank Adaptation): формулировка ΔW = AB
QLoRA: квантизация + LoRA для обучения на потребительском железе
IA³, DoRA и другие современные методы
Когда использовать полный fine-tuning, а когда PEFT

5.3 Современные фундаментальные модели

Семейства: LLaMA, Mistral, Gemma, Qwen, Command R
Специализированные модели: медицина, право, код
Мультимодальность: CLIP, Flamingo, LLaVA, GPT-4V


📄 Ключевые работы: Hu et al. (2022) LoRA; Hoffmann et al. (2022) Chinchilla; Touvron et al. (2023) LLaMA


Тема 6. Генерация текста: стратегии декодирования
6.1 Детерминированные методы

Greedy decoding: проблема локального оптимума
Beam search: ширина луча, length penalty, diverse beam search

6.2 Вероятностные методы

Temperature sampling: влияние на остроту распределения
Top-k sampling
Top-p (nucleus) sampling: адаптивное усечение
Typical sampling, η-sampling

6.3 Специальные методы

Repetition penalty, presence/frequency penalty
Constrained decoding: grammars, GBNF
Speculative decoding: ускорение с помощью draft-модели


Тема 7. Оценка качества генерации текста
7.1 Метрики на основе n-грамм

BLEU: формулировка, brevity penalty, критика
ROUGE (ROUGE-N, ROUGE-L): применение в резюмировании
METEOR: учёт морфологии и синонимов
CIDEr: для задач image captioning

7.2 Нейронные метрики

BERTScore: cosine similarity в пространстве контекстуальных эмбеддингов
MoverScore, BARTScore
Gemba-MQM, COMET: обученные метрики для перевода

7.3 LLM-as-a-Judge

GPT-4 / Claude как автоматический оценщик
MT-Bench, AlpacaEval, Arena (Chatbot Arena / LMSYS)
Проблемы: позиционный bias, self-preference, gaming метрик


Тема 8. RLHF и выравнивание языковых моделей
8.1 Основы RLHF

Модель предпочтений (reward model): Bradley-Terry формулировка
PPO (Proximal Policy Optimization) в контексте LLM
KL-дивергенция как регуляризатор

8.2 Альтернативные методы выравнивания

DPO (Direct Preference Optimization): без явной reward-модели
IPO, KTO, SimPO — вариации и улучшения DPO
Constitutional AI (Anthropic): принципы + RLHF
RLAIF: использование LLM вместо человека-аннотатора

8.3 Instruction Fine-Tuning и промпт-инжиниринг

Форматы инструкций: Alpaca, ShareGPT, ChatML
Zero-shot, few-shot, many-shot learning
Chain-of-Thought (CoT), Tree-of-Thought (ToT), Graph-of-Thought
Self-consistency, ReAct, least-to-most prompting


📄 Ключевые работы: Ouyang et al. (2022) InstructGPT; Rafailov et al. (2023) DPO; Wei et al. (2022) CoT


Тема 9. Расширенный информационный поиск и Question Answering
9.1 Нейронные методы поиска

Dense Passage Retrieval (DPR): bi-encoder архитектура
ColBERT: late interaction для точного поиска
Hybrid retrieval: sparse (BM25) + dense

9.2 Retrieval-Augmented Generation (RAG)

Базовая RAG-архитектура: retrieve → read → generate
Advanced RAG: HyDE, re-ranking (cross-encoder), iterative retrieval
Modular RAG и Self-RAG (рефлексивная генерация)
Оценка RAG: RAGAS, TruLens

9.3 Question Answering

Extractive QA: SQuAD, BERT-based span extraction
Abstractive QA: генеративные модели
Multi-hop QA: HotpotQA, MuSiQue
Long-context QA: расширение контекстного окна (RoPE scaling, YaRN)


Тема 10. Генерация кода
10.1 Специфика кода как языка

Отличия от естественного языка: структура, синтаксис, семантика исполнения
Токенизация кода, специальные токены

10.2 Модели для кода

Codex, GitHub Copilot, Code LLaMA, DeepSeek Coder, StarCoder2
Fill-in-the-Middle (FIM) обучение
Execution feedback: обучение на результатах выполнения (CodeRL, AlphaCode)

10.3 Оценка и бенчмарки

HumanEval, MBPP, SWE-bench
Pass@k метрика
EvoEval, LiveCodeBench — динамические бенчмарки


Тема 11. Агентные системы на основе LLM
11.1 Основы LLM-агентов

Компоненты агента: LLM-мозг, память, инструменты, планировщик
ReAct (Reasoning + Acting): синергия размышлений и действий
Tool use / Function calling: JSON-схемы, параллельный вызов

11.2 Память и контекст

In-context (рабочая) память vs. внешняя (векторная БД)
Episodic, semantic, procedural memory в агентах
Компрессия контекста, summarization-based memory

11.3 Многоагентные системы

AutoGen, CrewAI, LangGraph: оркестрация агентов
Паттерны: supervisor, peer-to-peer, debate (SPP)
Агенты-специалисты vs. generalist-агент
Проблемы: hallucination cascade, бесконечные циклы, безопасность

11.4 Комплексное планирование и рассуждение

Plan-and-Execute, HuggingGPT, Voyager
Self-reflection и Reflexion (Shinn et al., 2023)
Monte Carlo Tree Search + LLM (AlphaProof-подход)


📄 Ключевые работы: Yao et al. (2023) ReAct; Shinn et al. (2023) Reflexion; Wu et al. (2023) AutoGen


Тема 12. Передовые исследования и открытые проблемы
12.1 Рассуждение и математика

Chain-of-Thought Scaling, Process Reward Models (PRM)
OpenAI o1/o3, DeepSeek R1: «думающие» модели (test-time compute)
Математические бенчмарки: MATH, GSM8K, AIME

12.2 Эффективность и развёртывание

Квантизация: GPTQ, AWQ, GGUF
Дистилляция знаний применительно к LLM
Speculative decoding, continuous batching (vLLM)

12.3 Безопасность и интерпретируемость

Jailbreak-атаки и защита
Mechanistic Interpretability: circuits, superposition, induction heads
Hallucination: причины, обнаружение, митигация
Watermarking и детекция AI-текста

12.4 Мультимодальность и следующие рубежи

Vision-Language Models: PaLM-E, GPT-4o, Gemini
Speech + Text: Whisper, SpeechT5, обработка аудио
World models и LLM как симуляторы


Практические работы и проекты
№ТемаИнструменты1Построение TF-IDF поискового движкаsklearn, whoosh2Обучение биграммной LM + Word2VecPyTorch, gensim3Seq2Seq NMT на RNN с attentionPyTorch4Fine-tuning BERT на задачу классификацииHuggingFace Transformers5LoRA fine-tuning LLaMA на инструкцияхPEFT, bitsandbytes6RAG-система с оценкой качестваLangChain/LlamaIndex, FAISS7Простой LLM-агент с инструментамиLangGraph / AutoGen8Курсовой проект (свободный выбор задачи)—

Рекомендуемая литература

Jurafsky & Martin. Speech and Language Processing (3rd ed., draft)
Tunstall et al. Natural Language Processing with Transformers (O'Reilly, 2022)
Zhao et al. A Survey of Large Language Models (2023, arxiv)
Wang et al. A Survey on Large Language Model based Autonomous Agents (2023)
Курсы: Stanford CS224N, CMU CS11-711, Hugging Face NLP Course
