# Encryption 加密技术

## 散列

> Hash，一般翻译做散列、杂凑，或音译为哈希，是把任意长度的[输入](https://baike.baidu.com/item/输入/5481954)（又叫做预映射 pre-image）通过散列算法变换成固定长度的[输出](https://baike.baidu.com/item/输出/11056752)，该输出就是散列值。这种转换是一种[压缩映射](https://baike.baidu.com/item/压缩映射/5114126)，也就是，散列值的空间通常远小于输入的空间，不同的输入可能会散列成相同的输出，所以不可能从散列值来确定唯一的输入值。简单的说就是一种将任意长度的消息压缩到某一固定长度的[消息摘要](https://baike.baidu.com/item/消息摘要/4547744)的函数。
>
> - 中文名
>
>   散列、杂凑
>
> - 外文名
>
>   Hash
>
> - 音 译
>
>   哈希
>
> - 释 义
>
>   把任意长度的[输入](https://baike.baidu.com/item/输入/5481954)通过散列算法变换成固定长度的[输出](https://baike.baidu.com/item/输出/11056752)
>
> - 属 性
>
>   压缩映射
>
> - 特 点
>
>   很难找到逆向规律

### 散列算法比较

| 名称  | 安全性 | 速度 |
| :---- | :----- | :--- |
| SHA-1 | 高     | 慢   |
| MD5   | 中     | 快   |

## 对称加密算法

> 对称加密算法是应用较早的加密算法，技术成熟。在对称加密算法中，数据发信方将明文（原始数据）和加密密钥（mi yao）一起经过特殊加密算法处理后，使其变成复杂的加密密文发送出去。收信方收到密文后，若想解读原文，则需要使用加密用过的密钥及相同算法的逆算法对密文进行解密，才能使其恢复成可读明文。在对称加密算法中，使用的密钥只有一个，发收信双方都使用这个密钥对数据进行加密和解密，这就要求解密方事先必须知道加密密钥。
>
> - 中文名
>
>   对称加密算法
>
> - 外文名
>
>   symmetric encryption algorithm

![symmetric-encryption.png](https://static.yoouu.cn/imgs/doc/basic/encryption/symmetric-encryption.png)

### 对称密钥：DES TripleDES 算法

DES 算法把 64 位的明文输入块变为数据长度为 64 位的密文输出块，其中 8 位为奇偶校验位，另外 56 位作为密码的长度。首先，DES 把输入的 64 位数据块按位重新组合，并把输出分为 L0、R0 两部分，每部分各长 32 位，并进行前后置换，最终由 L0 输出左 32 位，R0 输出右 32 位，根据这个法则经过 16 次迭代运算后，得到 L16、R16，将此作为输入，进行与初始置换相反的逆置换，即得到密文输出。 DES 算法具有极高的安全性，到目前为止，除了用穷举搜索法对 DES 算法进行攻击外，还没有发现更有效的办法，而 56 位长密钥的穷举空间为 2^56，这意味着如果一台计算机的速度是每秒种检测 100 万个密钥，那么它搜索完全部密钥就需要将近 2285 年的时间，因此 DES 算法是一种很可靠的加密方法。

### 对称密钥：RC 算法

RC4 算法的原理是“搅乱”，它包括初始化算法和伪随机子密码生成算法两大部分，在初始化的过程中，密钥的主要功能是将一个 256 字节的初始数簇进行随机搅乱，不同的数簇在经过伪随机子密码生成算法的处理后可以得到不同的子密钥序列，将得到的子密钥序列和明文进行异或运算（XOR）后，得到密文。由于 RC4 算法加密采用的是异或方式，所以，一旦子密钥序列出现了重复，密文就有可能被破解，但是目前还没有发现密钥长度达到 128 位的 RC4 有重复的可能性，所以，RC4 也是目前最安全的加密算法之一。

### 对称密钥：BlowFish 算法

BlowFish 算法是一个 64 位分组及可变密钥长度的分组密码算法，该算法是非专利的。 BlowFish 算法使用两个“盒”：pbox[18]和 sbox[4256]，BlowFish 算法有一个核心加密函数。该函数输入 64 位信息，运算后以 64 位密文的形式输出。用 BlowFish 算法加密信息，需要密钥预处理和信息加密两个过程。BlowFish 算法的原密钥 pbox 和 sbox 是固定的，要加密一个信息，需要选择一个 key，用这个 key 对 pbox 和 sbox 进行变换，得到下一步信息加密所用到的 key_pbox 和 key_sbox。 BlowFish 算法解密，同样也需要密钥预处理和信息解密两个过程。密钥预处理的过程和加密时完全相同。信息解密的过程就是把信息加密过程的 key_pbox 逆序使用即可。

### 对称加密算法比较

| 名称 | 密钥名称         | 运行速度 | 安全性 | 资源消耗 |
| :--- | :--------------- | :------- | :----- | :------- |
| DES  | 56 位            | 较快     | 低     | 中       |
| 3DES | 112 位或 168 位  | 慢       | 中     | 高       |
| AES  | 128、192、256 位 | 快       | 高     | 低       |

#### 对称算法

1. **密钥管理**：比较难，不适合互联网，一般用于内部系统
2. **安全性**：中
3. **加密速度**：快好 **几个数量级** (软件加解密速度至少快 `100` 倍，每秒可以加解密数 `M` **比特** 数据)，适合大数据量的加解密处理

## 应用模式

| 加密模式(英文名称及简写)   | 中文名称         |
| -------------------------- | ---------------- |
| Electronic Code Book(ECB)  | 电子密码本模式   |
| Cipher Block Chaining(CBC) | 密码分组链接模式 |
| Cipher Feedback Mode(CFB)  | 加密反馈模式     |
| Output Feedback Mode(OFB)  | 输出反馈模式     |

ECB：最基本的加密模式，也就是通常理解的加密，相同的明文将永远加密成相同的密文，无初始向量，容易受到密码本重放攻击，一般情况下很少用。

CBC：明文被加密前要与前面的密文进行异或运算后再加密，因此只要选择不同的初始向量，相同的密文加密后会形成不同的密文，这是目前应用最广泛的模式。CBC 加密后的密文是上下文相关的，但明文的错误不会传递到后续分组，但如果一个分组丢失，后面的分组将全部作废(同步错误)。

CFB：类似于自同步序列密码，分组加密后，按 8 位分组将密文和明文进行移位异或后得到输出同时反馈回移位寄存器，优点最小可以按字节进行加解密，也可以是 n 位的，CFB 也是上下文相关的，CFB 模式下，明文的一个错误会影响后面的密文(错误扩散)。

OFB：将分组密码作为同步序列密码运行，和 CFB 相似，不过 OFB 用的是前一个 n 位密文输出分组反馈回移位寄存器，OFB 没有错误扩散问题。

## 非对称加密算法

> **非对称加密算法**，又称为 **公开密钥加密算法**。它需要两个密钥，一个称为 **公开密钥** (`public key`)，即 **公钥**，另一个称为 **私有密钥** (`private key`)，即 **私钥**。
>
> 因为 **加密** 和 **解密** 使用的是两个不同的密钥，所以这种算法称为 **非对称加密算法**。
>
> - 中文名
>
>   非对称加密算法
>
> - 外文名
>
>   asymmetric cryptographic algorithm

![asymmetric-cryptographic.png](https://static.yoouu.cn/imgs/doc/basic/encryption/asymmetric-cryptographic.png)

### 非对称加密算法比较

| 名称 | 成熟度 | 安全性 | 运算速度 | 资源消耗 |
| :--- | :----- | :----- | :------- | :------- |
| RSA  |  高    | 高     | 中       | 中       |
| ECC  | 高     | 高     | 慢       | 高       |

#### 非对称算法

1. **密钥管理**：密钥容易管理
2. **安全性**：高
3. **加密速度**：比较慢，适合 **小数据量** 加解密或数据签名
