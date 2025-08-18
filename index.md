---
layout: base
title: I'm [Your Full Name]
hide: true
---

<style>
  /* 只保留必要的修改 */
  body {
    color: #333;
    background-color: #FFD1DC; /* 默认粉红色 */
    transition: background-color 1.5s ease;
  }
  
  .team-table {
    width: 100%;
    border-collapse: separate;
    border-spacing: 0;
    margin: 2rem 0;
    background: white;
    border-radius: 12px;
    overflow: hidden;
    box-shadow: 0 4px 20px rgba(0,0,0,0.08);
  }
  
  .team-table th {
    background: #6b4bd3;
    color: white;
    padding: 15px;
    text-align: left;
  }
  
  .team-table td {
    padding: 12px 15px;
    border-bottom: 1px solid #f0f0f0;
  }
  
  .team-table tr:hover {
    background-color: #f8f7ff;
  }
</style>

<script>
  // 简化的背景颜色变换
  const pastelColors = ['#FFD1DC', '#B5EAD7', '#C7CEEA'];
  let currentIndex = 0;
  
  function changeBackground() {
    document.body.style.backgroundColor = pastelColors[currentIndex];
    currentIndex = (currentIndex + 1) % pastelColors.length;
    setTimeout(changeBackground, 3000);
  }
  
  // 启动颜色变换
  setTimeout(changeBackground, 3000);
</script>

<!-- 保持您原有的内容不变，只替换表格部分 -->
<table class="team-table">
  <thead>
    <tr>
      <th>Role</th>
      <th>Name</th>
      <th>Repo Location</th>
      <th>Stream</th>
      <th>Repo Name</th>
    </tr>
  </thead>
  <tbody>
    <!-- 您的表格行数据 -->
  </tbody>
</table>

<!-- 其他原有内容保持不变 -->