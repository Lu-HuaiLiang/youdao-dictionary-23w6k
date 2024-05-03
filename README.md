# youdao-dictionary-23w6k 有什么？
里面有23w6k条有道英语单词信息的SQL文件，可以直接导入到数据库。

表信息 word-dict
```sql
CREATE TABLE `word_expand` (
  `word` varchar(64) COLLATE utf8mb4_unicode_ci NOT NULL DEFAULT '',
  `dict` longtext COLLATE utf8mb4_unicode_ci NOT NULL,
  `createdAt` datetime(3) NOT NULL DEFAULT CURRENT_TIMESTAMP(3),
  `updatedAt` datetime(3) NOT NULL DEFAULT CURRENT_TIMESTAMP(3),
  UNIQUE KEY `word_word_key` (`word`),
  KEY `word_word_idx` (`word`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_unicode_ci
```

dict 所包含的单词信息内容结构体！
```ts
export interface IWordDetail {
  word: string;
  forms: string[];
  explain_list: {
    pos: string;
    meaning: string;
  }[];
  pronounces: {
    type: string;
    phonetic: string;
    audio: {
      audio_url: string;
    };
  }[];
  synonyms: {
    cn_text: string;
    word: string[];
  };
  phrases: {
    text: string;
    trans: string[];
  }[];
  sentences: {
    text: string;
    tran: string;
    audio: {
      audio_url: string;
    };
    text_indexes: {
      start: number;
      end: number;
    }[];
  }[];
}
```

## 大文件是如何上传github的？
可以看一下这个 https://git-lfs.com/
支持100MB的大文件上传!!!
