---
{"dg-publish":true,"permalink":"/👀Personal/CTF stats/"}
---

# Stats
## Flags per categories and overall progression
<canvas height="0" width="0" style="display: block; box-sizing: border-box; height: 0px; width: 0px;"></canvas>



<script src="https://cdn.jsdelivr.net/npm/chart.js"></script>


<div>
  <canvas id="myChart"></canvas>
</div>



<script>


const ctx = document.getElementById('myChart');

const data = [
	{rev:0, pwn:0, oth:0, osi:5, ste:0, pro:0, mis:6, web:0, cry:1, for:0},
	{rev:0, pwn:0, oth:0, osi:0, ste:0, pro:0, mis:0, web:0, cry:0, for:0},
	{rev:0, pwn:0, oth:0, osi:0, ste:0, pro:0, mis:1, web:0, cry:0, for:0},
	{rev:1, pwn:0, oth:0, osi:1, ste:0, pro:3, mis:0, web:2, cry:1, for:1},
	{rev:1, pwn:0, oth:0, osi:0, ste:0, pro:0, mis:1, web:0, cry:0, for:0},
	{rev:2, pwn:0, oth:0, osi:6, ste:0, pro:0, mis:3, web:0, cry:0, for:0}
]

let summedData = [0,0,0,0,0,0,0,0,0,0]
const ks = ['rev', 'pwn', 'oth', 'osi', 'ste', 'pro', 'mis', 'web', 'cry', 'for']
data.forEach((d) => {
	i=0
	ks.forEach((k) => {
		summedData[i] += d[k]
		i++
	})
})

const labels = ['Reverse', 'Pwn', 'Other', 'OSINT', 'Steg', 'Programming', 'Misc', 'Web', 'Crypto', 'Forensics']

const bkCols = ['#D741A7','#892C8D','#3A1772','#475898','#5398BE','#7BA6A6','#A3B38E','#F2CD5D','#E8B954','#DEA54B']


/*const chartData = {
  
};*/

new Chart(ctx, {
type: 'polarArea',
  data: {
	  labels: labels,
	  datasets: [{
		  label: 'Polar graph of flags per categories',
		  data: summedData,
		  backgroundColor: bkCols
	  }]
  }
})

//window.renderChart(chartData, this.container);

</script>
