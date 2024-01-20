---
{"dg-publish":true,"permalink":"/👀Personal/CTF stats/"}
---

# Stats
## Flags per categories and overall progression

<script src="https://cdn.jsdelivr.net/npm/chart.js"></script>


<div>
  <canvas id="HistoChart"></canvas>
</div>

<div>
  <canvas id="NicePolarChart"></canvas>
</div>




<script>


const ctx = document.getElementById('NicePolarChart');

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






<script>


const ctxh = document.getElementById('HistoChart');

const dataH = {
    labels: ['Category 1', 'Category 2'],
    datasets: [
      {
        label: 'Subcategory 1',
        data: [10, 40],
        backgroundColor: 'rgba(255, 99, 132, 0.7)',
        borderWidth: 1
      },
      {
        label: 'Subcategory 2',
        data: [20, 50],
        backgroundColor: 'rgba(54, 162, 235, 0.7)',
        borderWidth: 1
      },
      {
        label: 'Subcategory 3',
        data: [30, 60],
        backgroundColor: 'rgba(255, 206, 86, 0.7)',
        borderWidth: 1
      }
    ]
  };

  const options = {
    indexAxis: 'y',
    plugins: {
      legend: {
        position: 'bottom'
      }
    }
  };

  const marimekkoChart = new Chart(ctxh, {
    type: 'bar',
    data: dataH,
  });


</script>