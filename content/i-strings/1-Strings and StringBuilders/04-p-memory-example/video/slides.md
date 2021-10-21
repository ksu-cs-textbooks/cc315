---
type: "reveal"
hidden: true
---


<section>
<img class="stretch plain" src="/cc315/images/0/core-logo-on-white.svg">
<h3> Module 1 <br> Strings and StringBuilders <br> Character Arrays</h3>
<hr style="height:15px;color:512888;background-color:512888;">
<h4>CC315</h4>
</section>

<!--- s2 --->
<section>
	<h3>Array of Strings</h3>
     <pre class="" style="font-size: .3em"><code class="python"> arr = ["a","b","abc"]</code></pre>
</section>

<!--- s3 --->
<section>
	<h3>Array of Strings</h3>
     <pre class="" style="font-size: .3em"><code class="python">arr = []
arr.append("foo")
arr.append("1234") # here arr == ["foo","1234"]
length = len(arr) # will result in 2
string_arr = "".join(arr) # will result in "foo1234"
</code></pre>
</section>

<!--- s4 --->
<section>
	<h3>With Strings</h3>
    <pre class="" style="font-size: .3em"><code class="python">
    function ENCODER(TEXT,X)
        #TEXT is the text to encode
        #X is the offset
        ENC = ""
        loop I from 1 to LENGTH of TEXT
            CURRENT = TEXT[I]
            IF CURRENT IS A LETTER
                CHAR_ENC = GET X-th CHAR after CURRENT
                ENC += CHAR_ENC
            ELSE
                ENC += '*'
        end loop
        return ENC
    end function
 </code></pre>
 	<h3>With Array of Strings</h3>
    <pre class="" style="font-size: .3em"><code class="python">
    function ARR_ENCODER(TEXT,X)
        #TEXT is the text to encode
        #X is the offset
        ENC = []
        loop I from 1 to LENGTH of TEXT
            CURRENT = TEXT[I]
            IF CURRENT IS A LETTER
                CHAR_ENC = GET X-th CHAR after CURRENT
                ENC.append(CHAR_ENC)
            ELSE
                ENC.append('*')
        end loop
        return "".join(ENC)
    end function
 </code></pre>
</section>


<!--- s5 --->
<section>
	<h3>With Strings</h3>
    <pre class="" style="font-size: .3em"><code class="python">
    function ENCODER(TEXT,X)
        #TEXT is the text to encode
        #X is the offset
        <mark>ENC = ""</mark>
        loop I from 1 to LENGTH of TEXT
            CURRENT = TEXT[I]
            IF CURRENT IS A LETTER
                CHAR_ENC = GET X-th CHAR after CURRENT
                <mark>ENC += CHAR_ENC</mark>
            ELSE
               <mark> ENC += '*'</mark>
        end loop
        <mark>return ENC</mark>
    end function
 </code></pre>
 	<h3>With Array of Strings</h3>
    <pre class="" style="font-size: .3em"><code class="python">
    function ARR_ENCODER(TEXT,X)
        #TEXT is the text to encode
        #X is the offset
        <mark>ENC = []</mark>
        loop I from 1 to LENGTH of TEXT
            CURRENT = TEXT[I]
            IF CURRENT IS A LETTER
                CHAR_ENC = GET X-th CHAR after CURRENT
                <mark>ENC.append(CHAR_ENC)</mark>
            ELSE
                <mark>ENC.append('*')</mark>
        end loop
        <mark>return "".join(ENC)</mark>
    end function
 </code></pre>
</section>

<!--- s6--->
<section>
 	<h3>Array of Strings Walk Through</h3>
    <pre class="" style="font-size: .3em"><code class="python">
    function ARR_ENCODER(TEXT,X)        # call ARR_ENCODER("Data is great!",8)
        #TEXT is the text to encode
        #X is the offset
        <mark>ENC = []</mark>
        loop I from 1 to LENGTH of TEXT
            CURRENT = TEXT[I]
            IF CURRENT IS A LETTER
                CHAR_ENC = GET X-th CHAR after CURRENT
                ENC.append(CHAR_ENC)
            ELSE
                ENC.append('*')
        end loop
        return "".join(ENC)
    end function
 </code></pre>
 <img class="stretch plain" src="/cc315/images/1/315SBmem_map1.png">
</section>

<!--- s7--->
<section>
 	<h3>Array of Strings Walk Through</h3>
    <pre class="" style="font-size: .3em"><code class="python">
    function ARR_ENCODER(TEXT,X)        # call ARR_ENCODER("<mark>D</mark>ata is great!",8)
        #TEXT is the text to encode
        #X is the offset
        ENC = []
        <mark>loop I from 1 to LENGTH of TEXT</mark>
            CURRENT = TEXT[I]
            IF CURRENT IS A LETTER
                CHAR_ENC = GET X-th CHAR after CURRENT
                ENC.append(CHAR_ENC)
            ELSE
                ENC.append('*')
        end loop
        return "".join(ENC)
    end function
 </code></pre>
 <img class="stretch plain" src="/images/315SBmem_map1.png">
</section>

<!--- s8--->
<section>
 	<h3>Array of Strings Walk Through</h3>
    <pre class="" style="font-size: .3em"><code class="python">
    function ARR_ENCODER(TEXT,X)        # call ARR_ENCODER("<mark>D</mark>ata is great!",8)
        #TEXT is the text to encode
        #X is the offset
        ENC = []
        loop I from 1 to LENGTH of TEXT
            CURRENT = TEXT[I]
            IF CURRENT IS A LETTER
                CHAR_ENC = GET X-th CHAR after CURRENT
                <mark>ENC.append(CHAR_ENC)</mark>
            ELSE
                ENC.append('*')
        end loop
        return "".join(ENC)
    end function
 </code></pre>
 <img class="stretch plain" src="/cc315/images/1/315SBmem_map2.png">
</section>

<!--- s9 --->
<section>
 	<h3>Array of Strings Walk Through</h3>
    <pre class="" style="font-size: .3em"><code class="python">
    function ARR_ENCODER(TEXT,X)        # call ARR_ENCODER("D<mark>a</mark>ta is great!",8)
        #TEXT is the text to encode
        #X is the offset
        ENC = []
        loop I from 1 to LENGTH of TEXT
            CURRENT = TEXT[I]
            IF CURRENT IS A LETTER
                CHAR_ENC = GET X-th CHAR after CURRENT
                <mark>ENC.append(CHAR_ENC)</mark>
            ELSE
                ENC.append('*')
        end loop
        return "".join(ENC)
    end function
 </code></pre>
 <img class="stretch plain" src="/images/315SBmem_map3.png">
</section>

<!--- s10 --->
<section>
 	<h3>Array of Strings Walk Through</h3>
    <pre class="" style="font-size: .3em"><code class="python">
    function ARR_ENCODER(TEXT,X)        # call ARR_ENCODER("Da<mark>t</mark>a is great!",8)
        #TEXT is the text to encode
        #X is the offset
        ENC = []
        loop I from 1 to LENGTH of TEXT
            CURRENT = TEXT[I]
            IF CURRENT IS A LETTER
                CHAR_ENC = GET X-th CHAR after CURRENT
                <mark>ENC.append(CHAR_ENC)</mark>
            ELSE
                ENC.append('*')
        end loop
        return "".join(ENC)
    end function
 </code></pre>
 <img class="stretch plain" src="/cc315/images/1/315SBmem_map4.png">
</section>

<!--- s11 --->
<section>
 	<h3>Fast Forward</h3>
    <pre class="" style="font-size: .3em"><code class="python">
    function ARR_ENCODER(TEXT,X)        # call ARR_ENCODER("Data is great<mark>!</mark>",8)
        #TEXT is the text to encode
        #X is the offset
        ENC = []
        loop I from 1 to LENGTH of TEXT
            CURRENT = TEXT[I]
            IF CURRENT IS A LETTER
                CHAR_ENC = GET X-th CHAR after CURRENT
                ENC.append(CHAR_ENC)
            ELSE
                ENC.append('*')
        <mark>end loop</mark>
        return "".join(ENC)
    end function
 </code></pre>
 <img class="stretch plain" src="/images/315SBmem_map5.png">
</section>

<!--- s12 --->
<section>
 	<h3>Fast Forward</h3>
    <pre class="" style="font-size: .3em"><code class="python">
    function ARR_ENCODER(TEXT,X)        # call ARR_ENCODER("Data is great!",8)
        #TEXT is the text to encode
        #X is the offset
        ENC = []
        loop I from 1 to LENGTH of TEXT
            CURRENT = TEXT[I]
            IF CURRENT IS A LETTER
                CHAR_ENC = GET X-th CHAR after CURRENT
                ENC.append(CHAR_ENC)
            ELSE
                ENC.append('*')
        end loop
        <mark>return "".join(ENC)</mark>
    end function
 </code></pre>
 <img class="stretch plain" src="/cc315/images/1/315SBmem_map6.png">
</section>


<section> 
<h4>Comparison: <br/> String (S) VS Array of Strings (ARR)</h4>
<small>
<table>
  <tr>
    <th>Iterations</th>
    <th colspan="2" >Character Copies</th>
    <th colspan="2">Memory Addresses</th>
  </tr>
  <tr>
    <th> </th>
    <th> S </th>
    <th> ARR </th>
    <th> S </th>
    <th> ARR </th>
  </tr>
    <tr>
    <td> n </td>
    <td> (n(n+1))/2 </td>
    <td> n </td>
    <td> n + 1 </td>
    <td> 1 </td>
  </tr>
    <tr>
    <td> 1,000,000 </td>
    <td> 500,000,500,000 </td>
    <td> 1,000,000 </td>
    <td> 1,000,001 </td>
    <td> 1 </td>
  </tr>
</table>
</small>




<section>
