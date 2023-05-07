<template>
  <div class="home">
    <!-- <img alt="Vue logo" src="../assets/logo.png"> -->
    <!-- <HelloWorld msg="Welcome to Your Vue.js App" time="5000" /> -->
    <div>fast</div>
  </div>
</template>

<script>
// @ is an alias to /src
import HelloWorld from '@/components/HelloWorld.vue'

export default {
  name: 'Home',
  components: {
    HelloWorld
  },
  data() {
    return {
      temptxt: 'hello'
    }
  },
  computed: {
    count: function () {
      return this.$store._state.data.module1.count
    }
  },
  created() {
    var that = this
    console.log('temptxt', that.count)
    this.algorithmJs()
  },
  mounted() {},
  methods: {
    test() {},
    algorithmJs() {
      console.log('algorithmJs')

      // this.longestCommonSubsequence('kabc', 'dddxxkabzzz')
      this.longestPalindrome("babad")
    },

    //最长回文子串
    longestPalindrome(s) {
      const n = s.length
      let longest = ''
      const dp = Array(n)
        .fill()
        .map(() => Array(n).fill(false))
        // console.log(dp);

      for (let i = n - 1; i >= 0; i--) {
        for (let j = i; j < n; j++) {
          dp[i][j] = s[i] === s[j] && (j - i < 2 || dp[i + 1][j - 1])
          if (dp[i][j] && j - i + 1 > longest.length) {
            longest = s.substring(i, j + 1)
          }
        }
      }

      return longest
    },
    //最长公共子序列
    longestCommonSubsequence(str1, str2) {
      const m = str1.length
      const n = str2.length
      const dp = new Array(m + 1).fill(0).map(() => new Array(n + 1).fill(0))
      // console.log('dp',dp,new Array(m + 1).fill(0));
      for (let i = 1; i <= m; i++) {
        for (let j = 1; j <= n; j++) {
          if (str1[i - 1] === str2[j - 1]) {
            dp[i][j] = dp[i - 1][j - 1] + 1
            console.log('eq', i, j, str1[i - 1], str2[j - 1], dp[i][j], dp)
          } else {
            dp[i][j] = Math.max(dp[i][j - 1], dp[i - 1][j])
          }
        }
      }
      return dp[m][n]
    },

    
  }
}
</script>
