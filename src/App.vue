<script setup>
import { ref } from 'vue'
import HelloWorld from './components/HelloWorld.vue'

const recipes = [
  // 川菜
  { name: '麻婆豆腐', cuisine: '川菜', description: '川菜代表，麻辣鲜香，豆腐嫩滑', image: 'https://images.unsplash.com/photo-1582552938357-32b906df40cb?w=400', steps: [
    '准备食材：嫩豆腐、猪肉末、郫县豆瓣酱、花椒、葱花',
    '豆腐切块，放入沸水中焯烫，沥干备用',
    '热锅下油，爆香花椒，加入猪肉末炒至变色',
    '加入豆瓣酱炒香，加入适量清水',
    '放入豆腐块，大火烧开后转中小火煮3-5分钟',
    '最后加入淀粉勾芡，撒上葱花即可'
  ] },
  { name: '回锅肉', cuisine: '川菜', description: '咸鲜回甘，肥而不腻', image: 'https://images.unsplash.com/photo-1541832676-9b763b0239ab?w=400', steps: [
    '准备五花肉，切片，加入料酒、姜片焯水',
    '锅中放油，将肉片煸炒至表面金黄',
    '加入郫县豆瓣酱炒香',
    '加入蒜苗、青椒翻炒',
    '最后加入适量生抽、盐调味即可'
  ] },
  { name: '水煮鱼', cuisine: '川菜', description: '麻辣鲜香，鱼肉鲜嫩', image: 'https://images.unsplash.com/photo-1563245372-f21724e3856d?w=400', steps: [
    '草鱼片去骨切片，加入料酒、姜丝腌制15分钟',
    '准备豆芽、芹菜等配菜',
    '锅中放油，爆香花椒、干辣椒',
    '加入豆瓣酱炒香，加入适量清水',
    '放入配菜和鱼片，大火烧开',
    '最后撒上葱花、香菜即可'
  ] },
  { name: '宫保鸡丁', cuisine: '川菜', description: '鸡肉鲜嫩，花生香脆', image: 'https://images.unsplash.com/photo-1572862905000-c5b6244027a5?w=400', steps: [
    '鸡肉切丁，加入料酒、生抽腌制',
    '准备花生米、干辣椒、葱姜蒜',
    '热锅爆香花生米，取出备用',
    '爆香干辣椒、花椒，加入鸡丁翻炒',
    '加入调味料，最后加入花生米即可'
  ] },
  { name: '夫妻肺片', cuisine: '川菜', description: '香辣爽口，层次丰富', image: 'https://images.unsplash.com/photo-1569058242567-93de6f36f8eb?w=400', steps: [
    '牛肉、牛杂焯水后切片',
    '准备辣椒油、花生碎、芝麻',
    '调制麻辣酱料',
    '将肉片拌入酱料',
    '最后撒上花生碎、芝麻点缀'
  ] },
  { name: '鱼香肉丝', cuisine: '川菜', description: '咸甜酸辣，味道协调', image: 'https://images.unsplash.com/photo-1585937421612-70a008356fbe?w=400', steps: [
    '猪里脊切丝，加入料酒腌制',
    '准备胡萝卜、木耳、青椒切丝',
    '热锅炒香蒜末、姜末',
    '加入肉丝炒至变色',
    '加入配菜和调味料翻炒均匀'
  ] },
  
  // 粤菜
  { name: '白切鸡', cuisine: '粤菜', description: '鸡肉嫩滑，配以姜葱酱', image: 'https://images.unsplash.com/photo-1562967916-eb82221dfb92?w=400', steps: [
    '选用三黄鸡，加入葱姜焯水',
    '放入冷水中浸泡',
    '准备姜葱蒜蓉调味料',
    '鸡肉切块，淋上调味料即可'
  ] },
  { name: '蜜汁叉烧', cuisine: '粤菜', description: '甜咸适中，肉质鲜美', image: 'https://images.unsplash.com/photo-1582878826629-29b7ad1cdc43?w=400', steps: [
    '猪里脊切条，加入叉烧酱腌制4小时',
    '烤箱预热200度',
    '将腌制好的肉条放入烤盘',
    '烤制20分钟，中途翻面并刷蜜糖',
    '取出后切片即可'
  ] },
  { name: '清蒸鱼', cuisine: '粤菜', description: '保持原汁原味，鱼肉鲜美', image: 'https://images.unsplash.com/photo-1546069901-5ec6a79120b0?w=400', steps: [
    '鲜活鱼清洗干净，腹部划刀',
    '放入姜片、葱段',
    '大火将水烧开后放入鱼',
    '蒸制8-10分钟',
    '淋上热油，撒上葱花、姜丝即可'
  ] },
  { name: '虾饺', cuisine: '粤菜', description: '皮薄馅嫩，晶莹剔透', image: 'https://images.unsplash.com/photo-1563245372-f21724e3856d?w=400', steps: [
    '虾仁剁碎，加入调味料',
    '和面制作饺子皮',
    '包制虾饺',
    '蒸锅大火将水烧开',
    '蒸制3-4分钟即可'
  ] },
  { name: '烧鹅', cuisine: '粤菜', description: '皮脆肉嫩，香气四溢', image: 'https://images.unsplash.com/photo-1598103442097-8b74394b95c6?w=400', steps: [
    '鹅肉腌制入味',
    '晾干表面水分',
    '涂抹酱料',
    '挂在烤架上烤制',
    '出炉后切块即可'
  ] },
  { name: '煲仔饭', cuisine: '粤菜', description: '锅气十足，米饭香糯', image: 'https://images.unsplash.com/photo-1551326844-4df70f78d0e9?w=400', steps: [
    '腊肠切片，腊肉切块',
    '米饭洗净浸泡',
    '煲仔内放油，铺上米饭',
    '放入腊味，开火煮制',
    '淋上酱油即可'
  ] },

  // 苏菜
  { name: '松鼠桂鱼', cuisine: '苏菜', description: '外酥内嫩，造型独特', image: 'https://images.unsplash.com/photo-1576577445504-6af96477db52?w=400', steps: [
    '鲜活桂鱼去骨，鱼肉划花刀',
    '裹上淀粉，炸至金黄',
    '准备番茄酱、白糖等酱汁',
    '将酱汁浇在鱼身上',
    '最后撒上松子点缀'
  ] },
  { name: '大闸蟹', cuisine: '苏菜', description: '蟹黄肥美，肉质鲜甜', image: 'https://images.unsplash.com/photo-1534766555764-ce878a5e3a2b?w=400', steps: [
    '挑选新鲜大闸蟹，清洗干净',
    '放入沸水中蒸制10-15分钟',
    '准备姜醋蘸料',
    '取出后晾凉',
    '食用时蘸料搭配即可'
  ] },
  { name: '盐水鸭', cuisine: '苏菜', description: '咸鲜适中，皮脆肉嫩', image: 'https://images.unsplash.com/photo-1551504734-5ee1c4a1479b?w=400', steps: [
    '鸭子清洗干净，加入盐水腌制',
    '准备香料包',
    '放入锅中煮制',
    '冷却后切块',
    '配以蒜蓉或酱油'
  ] },
  { name: '扬州炒饭', cuisine: '苏菜', description: '色香味俱全，料足味美', image: 'https://images.unsplash.com/photo-1551326844-4df70f78d0e9?w=400', steps: [
    '准备各种配料切丁',
    '煎制鸡蛋',
    '炒制配料',
    '加入隔夜米饭翻炒',
    '调味后即可出锅'
  ] },
  { name: '清炖狮子头', cuisine: '苏菜', description: '肉质细腻，汤汁浓郁', image: 'https://images.unsplash.com/photo-1515669097368-22e68427d265?w=400', steps: [
    '猪肉剁馅调味',
    '搓制成大肉丸',
    '锅中放油煎至表面金黄',
    '加入清汤慢炖',
    '最后加入青菜即可'
  ] },
  { name: '水晶虾仁', cuisine: '苏菜', description: '晶莹剔透，鲜嫩爽口', image: 'https://images.unsplash.com/photo-1565680018434-b583b0b3f89d?w=400', steps: [
    '虾仁去壳去虾线',
    '加入料酒、淀粉腌制',
    '沸水中焯烫',
    '过冰水定型',
    '配以蘸料食用'
  ] },
  
  // 鲁菜
  { name: '糖醋鲤鱼', cuisine: '鲁菜', description: '外酥里嫩，酸甜可口', image: 'https://images.unsplash.com/photo-1580476262798-bddd9f4b7369?w=400', steps: [
    '鲤鱼清洗，两面划花刀',
    '裹上淀粉炸至金黄',
    '调制糖醋汁',
    '浇在鱼身上',
    '撒上香菜点缀'
  ] },
  { name: '葱烧海参', cuisine: '鲁菜', description: '海参鲜美，葱香浓郁', image: 'https://images.unsplash.com/photo-1548943487-a2e4e43b4853?w=400', steps: [
    '海参泡发处理',
    '葱段爆香',
    '加入海参翻炒',
    '加入调味料',
    '收汁即可出锅'
  ] },
  { name: '九转大肠', cuisine: '鲁菜', description: '口感独特，营养丰富', image: 'https://images.unsplash.com/photo-1534939561126-855b8675edd7?w=400', steps: [
    '大肠彻底清洗',
    '焯水去腥',
    '加入调味料炖煮',
    '收汁调味',
    '撒上葱花即可'
  ] },
  { name: '红烧海螺', cuisine: '鲁菜', description: '鲜美可口，营养丰富', image: 'https://images.unsplash.com/photo-1563245372-f21724e3856d?w=400', steps: [
    '海螺清洗干净',
    '爆香葱姜蒜',
    '加入海螺翻炒',
    '加入调味料烧制',
    '收汁即可出锅'
  ] },
  { name: '山东煎饼', cuisine: '鲁菜', description: '外酥内软，香气四溢', image: 'https://images.unsplash.com/photo-1515669097368-22e68427d265?w=400', steps: [
    '调制面糊',
    '摊成薄饼',
    '刷上酱料',
    '撒上葱花',
    '折叠即可食用'
  ] },
  { name: '把子肉', cuisine: '鲁菜', description: '肥而不腻，入口即化', image: 'https://images.unsplash.com/photo-1572862905000-c5b6244027a5?w=400', steps: [
    '五花肉切块',
    '放入锅中煸炒',
    '加入调味料',
    '小火炖煮',
    '收汁即可出锅'
  ] }
]
const currentRecipe = ref(null)
const isAnimating = ref(false)
const isFlipped = ref(false)
let animationInterval

const startAnimation = () => {
  if (isAnimating.value) return
  
  isAnimating.value = true
  let index = 0
  
  // 快速切换菜品
  animationInterval = setInterval(() => {
    currentRecipe.value = recipes[index]
    index = (index + 1) % recipes.length
  }, 100)
  
  // 6秒后停止动画
  setTimeout(() => {
    clearInterval(animationInterval)
    isAnimating.value = false
    getRandomRecipe()
  }, 3000)
}

const getRandomRecipe = () => {
  const randomIndex = Math.floor(Math.random() * recipes.length)
  currentRecipe.value = recipes[randomIndex]
}

const toggleFlip = () => {
  if (!isAnimating.value) {
    isFlipped.value = !isFlipped.value
  }
}
</script>

<template>
  <div class="container">
    <h1>今天吃什么？</h1>
    <div class="recipe-container" v-if="currentRecipe" :class="{ 'animating': isAnimating, 'flipped': isFlipped }" @click="toggleFlip">
      <div class="recipe-card">
        <div class="front">
          <div class="cuisine-tag">{{ currentRecipe.cuisine }}</div>
          <img :src="currentRecipe.image" :alt="currentRecipe.name" class="recipe-image">
          <h2>{{ currentRecipe.name }}</h2>
          <p>{{ currentRecipe.description }}</p>
        </div>
        <div class="back">
          <h2>{{ currentRecipe.name }} 的制作步骤</h2>
          <div class="steps-container">
            <ol>
              <li v-for="(step, index) in currentRecipe.steps" :key="index">{{ step }}</li>
            </ol>
          </div>
          <div class="flip-hint">点击卡片返回</div>
        </div>
      </div>
    </div>
    <button @click="startAnimation" class="random-btn" :disabled="isAnimating">
      {{ isAnimating ? '选择中...' : (currentRecipe ? '换一个' : '随机推荐') }}
    </button>
  </div>
</template>

<style scoped>
.container {
  max-width: 800px;
  margin: 0 auto;
  padding: 2rem;
  text-align: center;
  min-height: 100vh;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  gap: 2rem;
  background: #ffffff;
}

.recipe-container {
  margin: 0 auto 2rem;
  width: 100%;
  max-width: 400px;
  height: 600px;
  perspective: 1000px;
  cursor: pointer;
  position: relative;
}

.recipe-card {
  width: 100%;
  height: 100%;
  position: relative;
  transform-style: preserve-3d;
  transition: transform 0.6s;
}

.recipe-image {
  width: 100%;
  height: 250px;
  object-fit: cover;
  border-radius: 12px 12px 0 0;
  margin: 0;
  box-shadow: 0 5px 15px rgba(0, 0, 0, 0.1);
}

.front,
.back {
  position: absolute;
  width: 100%;
  height: 100%;
  backface-visibility: hidden;
  border-radius: 16px;
  background: white;
  box-shadow: 0 10px 20px rgba(0, 0, 0, 0.08);
  overflow: hidden;
  padding: 0;
  display: flex;
  flex-direction: column;
}

.front h2 {
  padding: 1rem 1.5rem 0.5rem;
  margin: 0;
}

.front p {
  padding: 0 1.5rem 1.5rem;
  margin: 0;
}

.back {
  transform: rotateY(180deg);
  padding: 1.5rem;
}

.recipe-container.flipped .recipe-card {
  transform: rotateY(180deg);
}

.steps-container {
  flex: 1;
  overflow-y: auto;
  text-align: left;
  padding: 1rem 0;
}

.steps-container ol {
  margin: 0;
  padding-left: 1.5rem;
}

.steps-container li {
  margin-bottom: 1rem;
  line-height: 1.6;
  color: #666;
}

.flip-hint {
  margin-top: 2rem;
  color: #42b883;
  font-size: 0.9rem;
  font-weight: 600;
}

@keyframes shake {
  0%, 100% { transform: translateX(0); }
  25% { transform: translateX(-5px); }
  75% { transform: translateX(5px); }
}

.cuisine-tag {
  position: absolute;
  top: 1rem;
  right: 1rem;
  background: rgba(66, 184, 131, 0.9);
  color: white;
  padding: 0.5rem 1rem;
  border-radius: 8px;
  font-weight: 600;
  font-size: 0.9rem;
  backdrop-filter: blur(4px);
  z-index: 1;
}



h2 {
  color: #2c3e50;
  font-size: 1.8rem;
  margin-bottom: 1rem;
  font-weight: 600;
}

p {
  color: #666;
  font-size: 1.1rem;
  line-height: 1.6;
  margin-bottom: 1.5rem;
}

.random-btn {
  position: relative;
  margin-top: 2rem;
  background: linear-gradient(135deg, #42b883 0%, #3aa876 100%);
  color: white;
  font-size: 1.1rem;
  padding: 0.8rem 2rem;
  border: none;
  border-radius: 12px;
  cursor: pointer;
  transition: all 0.3s ease;
  font-weight: 600;
  box-shadow: 0 4px 15px rgba(66, 184, 131, 0.3);
  min-width: 180px;
  letter-spacing: 0.5px;
  z-index: 10;
}

.random-btn:disabled {
  opacity: 0.7;
  cursor: not-allowed;
}

.random-btn:hover:not(:disabled) {
  transform: translateY(-2px);
  box-shadow: 0 6px 20px rgba(66, 184, 131, 0.4);
  background: linear-gradient(135deg, #3aa876 0%, #42b883 100%);
}

.random-btn:active:not(:disabled) {
  transform: translateY(0);
  box-shadow: 0 2px 10px rgba(66, 184, 131, 0.2);
}
</style>
