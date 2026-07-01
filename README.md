### picoCTF - MultiCode Writeup

\[Japanese / 日本語\]

### 概要

picoCTFのGeneral Skills分野にある問題「MultiCode」の解法（Writeup）です。この問題は、Base64、Hex（16進数）、ROT13といった複数のエンコード・暗号方式が組み合わされたメッセージを段階的にデコードしていく問題です。

### 解法手順

1.  **Base64のデコード**  
    ダウンロードした `message.txt` はBase64でエンコードされているため、デコードして16進数（Hex）の文字列を取り出します。
    
    bash
    
        base64 -d message.txt > step1.txt
        
    
    コードは注意してご使用ください。
    
2.  **16進数（Hex）のデコード**  
    取り出した16進数文字列を、プレーンテキストに変換します。
    
    bash
    
        xxd -r -p step1.txt > step2.txt
        
    
    コードは注意してご使用ください。
    
3.  **ROT13の復号**  
    変換後の文字列に対して、アルファベットを13文字ずらすROT13（シーザー暗号の一種）を適用します。
    
    bash
    
        cat step2.txt | tr 'A-Za-z' 'N-ZA-Mn-za-m' > step3.txt
        
    
    コードは注意してご使用ください。
    
4.  **特殊文字の置換（フラグの完成）**  
    最後に、URLエンコードされた括弧部分（`%7O` と `%7Q`）を、フラグの形式である `{` と `}` に置換することでフラグが完成します。
    
    bash
    
        cat step3.txt | sed 's/%7O/{/; s/%7Q/}/' > flag.txt
        
    
    コードは注意してご使用ください。
    

### 最終結果

text

    [picoCTF FLAG HIDDEN]
    

コードは注意してご使用ください。

* * *

\[English\]

### Overview

This is a writeup for the "MultiCode" challenge in the General Skills category of picoCTF. The challenge requires decoding a message that has been obfuscated using multiple layers of encoding: Base64, Hex (Hexadecimal), and ROT13.

### Solution Steps

1.  **Base64 Decoding**  
    The downloaded `message.txt` is encoded in Base64. Decode it to extract the Hex string.
    
    bash
    
        base64 -d message.txt > step1.txt
        
    
    コードは注意してご使用ください。
    
2.  **Hex Decoding**  
    Convert the extracted hexadecimal string into a plain text string.
    
    bash
    
        xxd -r -p step1.txt > step2.txt
        
    
    コードは注意してご使用ください。
    
3.  **ROT13 Decryption**  
    Apply ROT13 (a Caesar cipher variant that shifts letters by 13 places) to the decoded text.
    
    bash
    
        cat step2.txt | tr 'A-Za-z' 'N-ZA-Mn-za-m' > step3.txt
        
    
    コードは注意してご使用ください。
    
4.  **Replacing Special Characters (Final Flag)**  
    Finally, replace the URL-encoded brackets (`%7O` and `%7Q`) with the standard flag format `{` and `}` to reveal the flag.
    
    bash
    
        cat step3.txt | sed 's/%7O/{/; s/%7Q/}/' > flag.txt
        
    
    コードは注意してご使用ください。
    

### Final Result

text

    [picoCTF FLAG HIDDEN]
    

コードは注意してご使用ください。
