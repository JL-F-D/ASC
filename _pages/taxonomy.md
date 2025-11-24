---
layout: page
title: Taxonomy
permalink: /taxonomy/
description: Interactive taxonomy of trustworthy embodied AI
nav: true
nav_order: 2
---

<style>
.filter-btn {
  padding: 8px 16px;
  margin: 4px;
  border: 2px solid #007bff;
  background: white;
  color: #007bff;
  border-radius: 20px;
  cursor: pointer;
  font-size: 14px;
  transition: all 0.3s;
}
.filter-btn:hover, .filter-btn.active {
  background: #007bff;
  color: white;
}
.filter-section {
  margin: 20px 0;
}
.filter-label {
  font-weight: bold;
  margin-right: 10px;
}
.matrix-table {
  width: 100%;
  border-collapse: collapse;
  margin-top: 20px;
}
.matrix-table th, .matrix-table td {
  border: 1px solid #ddd;
  padding: 12px;
  text-align: center;
}
.matrix-table th {
  background: #f5f5f5;
  font-weight: bold;
}
.matrix-table td.cell {
  cursor: pointer;
  transition: all 0.3s;
}
.matrix-table td.cell:hover {
  background: #e3f2fd;
}
.matrix-table td.cell.highlight {
  background: #bbdefb;
}
.matrix-table td.empty {
  color: #ccc;
}
.row-header {
  background: #fafafa;
  font-weight: bold;
}
.hidden {
  display: none;
}

/* Modal 弹窗样式 */
.modal {
  display: none;
  position: fixed;
  top: 0; left: 0;
  width: 100%; height: 100%;
  background: rgba(0,0,0,0.5);
  z-index: 1000;
}
.modal-content {
  background: white;
  margin: 10% auto;
  padding: 30px;
  width: 60%;
  max-width: 600px;
  border-radius: 10px;
  position: relative;
}
.modal-close {
  position: absolute;
  top: 10px; right: 15px;
  font-size: 24px;
  cursor: pointer;
}
.paper-list {
  margin-top: 15px;
  text-align: left;
}
.paper-item {
  padding: 10px;
  margin: 5px 0;
  background: #f9f9f9;
  border-radius: 5px;
}
</style>

<div class="filter-section">
  <span class="filter-label">属性筛选：</span>
  <button class="filter-btn active" onclick="filterRow('all')">全部</button>
  <button class="filter-btn" onclick="filterRow('privacy')">Privacy</button>
  <button class="filter-btn" onclick="filterRow('safety')">Safety</button>
  <button class="filter-btn" onclick="filterRow('explainability')">Explainability</button>
  <button class="filter-btn" onclick="filterRow('fairness')">Fairness</button>
  <button class="filter-btn" onclick="filterRow('robustness')">Robustness</button>
  <button class="filter-btn" onclick="filterRow('generalization')">Generalization</button>
  <button class="filter-btn" onclick="filterRow('efficiency')">Efficiency</button>
  <button class="filter-btn" onclick="filterRow('human-centric')">Human-Centric</button>
</div>

<div class="filter-section">
  <span class="filter-label">模块筛选：</span>
  <button class="filter-btn active" onclick="filterCol('all')">全部</button>
  <button class="filter-btn" onclick="filterCol('instruction')">Instruction Understanding</button>
  <button class="filter-btn" onclick="filterCol('perception')">Environment Perception</button>
  <button class="filter-btn" onclick="filterCol('planning')">Action Planning</button>
  <button class="filter-btn" onclick="filterCol('interaction')">Physical Interaction</button>
</div>

<table class="matrix-table" id="taxonomyTable">
  <thead>
    <tr>
      <th>属性</th>
      <th data-col="instruction">Instruction Understanding</th>
      <th data-col="perception">Environment Perception</th>
      <th data-col="planning">Action Planning</th>
      <th data-col="interaction">Physical Interaction</th>
    </tr>
  </thead>
  <tbody>
    <tr data-row="privacy">
      <td class="row-header">Privacy</td>
      <td class="cell" data-col="instruction" onclick="showPapers('privacy', 'instruction')">指令隐私保护</td>
      <td class="cell" data-col="perception" onclick="showPapers('privacy', 'perception')">感知隐私保护</td>
      <td class="cell" data-col="planning" onclick="showPapers('privacy', 'planning')">联邦规划</td>
      <td class="cell" data-col="interaction" onclick="showPapers('privacy', 'interaction')">现场隐私保护</td>
    </tr>
    <tr data-row="safety">
      <td class="row-header">Safety</td>
      <td class="cell" data-col="instruction" onclick="showPapers('safety', 'instruction')">指令安全检测</td>
      <td class="cell" data-col="perception" onclick="showPapers('safety', 'perception')">对抗攻击防御</td>
      <td class="cell" data-col="planning" onclick="showPapers('safety', 'planning')">安全约束规划</td>
      <td class="cell" data-col="interaction" onclick="showPapers('safety', 'interaction')">安全操控</td>
    </tr>
    <tr data-row="explainability">
      <td class="row-header">Explainability</td>
      <td class="cell" data-col="instruction" onclick="showPapers('explainability', 'instruction')">语义消歧</td>
      <td class="cell" data-col="perception" onclick="showPapers('explainability', 'perception')">场景可视化</td>
      <td class="cell" data-col="planning" onclick="showPapers('explainability', 'planning')">可解释推理</td>
      <td class="cell" data-col="interaction" onclick="showPapers('explainability', 'interaction')">行为审计</td>
    </tr>
    <tr data-row="fairness">
      <td class="row-header">Fairness</td>
      <td class="cell" data-col="instruction" onclick="showPapers('fairness', 'instruction')">数据偏见</td>
      <td class="cell" data-col="perception" onclick="showPapers('fairness', 'perception')">公平识别</td>
      <td class="cell" data-col="planning" onclick="showPapers('fairness', 'planning')">公平决策</td>
      <td class="cell" data-col="interaction" onclick="showPapers('fairness', 'interaction')">伦理交互</td>
    </tr>
    <tr data-row="robustness">
      <td class="row-header">Robustness</td>
      <td class="cell" data-col="instruction" onclick="showPapers('robustness', 'instruction')">不确定性处理</td>
      <td class="cell" data-col="perception" onclick="showPapers('robustness', 'perception')">多模态鲁棒</td>
      <td class="cell" data-col="planning" onclick="showPapers('robustness', 'planning')">容错规划</td>
      <td class="cell" data-col="interaction" onclick="showPapers('robustness', 'interaction')">物理鲁棒性</td>
    </tr>
    <tr data-row="generalization">
      <td class="row-header">Generalization</td>
      <td class="cell" data-col="instruction" onclick="showPapers('generalization', 'instruction')">跨域指令</td>
      <td class="cell" data-col="perception" onclick="showPapers('generalization', 'perception')">跨环境感知</td>
      <td class="cell" data-col="planning" onclick="showPapers('generalization', 'planning')">零样本规划</td>
      <td class="cell" data-col="interaction" onclick="showPapers('generalization', 'interaction')">仿真到真实</td>
    </tr>
    <tr data-row="efficiency">
      <td class="row-header">Efficiency</td>
      <td class="cell empty" data-col="instruction">-</td>
      <td class="cell empty" data-col="perception">-</td>
      <td class="cell" data-col="planning" onclick="showPapers('efficiency', 'planning')">低时延推理</td>
      <td class="cell" data-col="interaction" onclick="showPapers('efficiency', 'interaction')">边缘部署</td>
    </tr>
    <tr data-row="human-centric">
      <td class="row-header">Human-Centric</td>
      <td class="cell empty" data-col="instruction">-</td>
      <td class="cell empty" data-col="perception">-</td>
      <td class="cell empty" data-col="planning">-</td>
      <td class="cell" data-col="interaction" onclick="showPapers('human-centric', 'interaction')">人机协作</td>
    </tr>
  </tbody>
</table>

<!-- 弹窗 -->
<div class="modal" id="paperModal">
  <div class="modal-content">
    <span class="modal-close" onclick="closeModal()">&times;</span>
    <h3 id="modalTitle">相关论文</h3>
    <div class="paper-list" id="paperList"></div>
  </div>
</div>

<script>
// 论文数据（你可以在这里添加每个格子对应的论文）
const papers = {
  'privacy-instruction': [
    {title: '论文1标题', author: '作者', year: 2024, link: '#'},
    {title: '论文2标题', author: '作者', year: 2023, link: '#'},
  ],
  'privacy-perception': [
    {title: '感知隐私保护论文', author: '作者', year: 2024, link: '#'},
  ],
  'safety-instruction': [
    {title: '指令安全检测论文', author: '作者', year: 2024, link: '#'},
  ],
  // ... 添加更多论文数据
};

let currentRowFilter = 'all';
let currentColFilter = 'all';

function filterRow(row) {
  currentRowFilter = row;
  applyFilters();
  updateButtons('row', row);
}

function filterCol(col) {
  currentColFilter = col;
  applyFilters();
  updateButtons('col', col);
}

function applyFilters() {
  const rows = document.querySelectorAll('tbody tr');
  rows.forEach(tr => {
    const rowType = tr.getAttribute('data-row');
    const showRow = (currentRowFilter === 'all' || rowType === currentRowFilter);
    tr.style.display = showRow ? '' : 'none';
  });

  const allCells = document.querySelectorAll('td[data-col], th[data-col]');
  const colIndex = {instruction: 1, perception: 2, planning: 3, interaction: 4};
  
  if (currentColFilter === 'all') {
    allCells.forEach(cell => cell.style.display = '');
    document.querySelectorAll('th, td').forEach((cell, i) => cell.style.display = '');
  } else {
    const idx = colIndex[currentColFilter];
    document.querySelectorAll('tr').forEach(tr => {
      const cells = tr.children;
      for (let i = 1; i < cells.length; i++) {
        cells[i].style.display = (i === idx) ? '' : 'none';
      }
    });
  }
}

function updateButtons(type, value) {
  const section = type === 'row' ? 0 : 1;
  const buttons = document.querySelectorAll('.filter-section')[section].querySelectorAll('.filter-btn');
  buttons.forEach(btn => btn.classList.remove('active'));
  event.target.classList.add('active');
}

function showPapers(row, col) {
  const key = `${row}-${col}`;
  const paperData = papers[key] || [];
  
  document.getElementById('modalTitle').textContent = `${row} × ${col}`;
  
  const listDiv = document.getElementById('paperList');
  if (paperData.length === 0) {
    listDiv.innerHTML = '<p>暂无论文数据，请在代码中添加</p>';
  } else {
    listDiv.innerHTML = paperData.map(p => `
      <div class="paper-item">
        <strong><a href="${p.link}">${p.title}</a></strong><br>
        <small>${p.author} (${p.year})</small>
      </div>
    `).join('');
  }
  
  document.getElementById('paperModal').style.display = 'block';
}

function closeModal() {
  document.getElementById('paperModal').style.display = 'none';
}

window.onclick = function(e) {
  if (e.target === document.getElementById('paperModal')) {
    closeModal();
  }
}
</script>
