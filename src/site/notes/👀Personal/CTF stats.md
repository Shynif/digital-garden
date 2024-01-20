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

const datah = [
	{rev:0, pwn:0, oth:0, osi:5, ste:0, pro:0, mis:6, web:0, cry:1, for:0},
	{rev:0, pwn:0, oth:0, osi:0, ste:0, pro:0, mis:0, web:0, cry:0, for:0},
	{rev:0, pwn:0, oth:0, osi:0, ste:0, pro:0, mis:1, web:0, cry:0, for:0},
	{rev:1, pwn:0, oth:0, osi:1, ste:0, pro:3, mis:0, web:2, cry:1, for:1},
	{rev:1, pwn:0, oth:0, osi:0, ste:0, pro:0, mis:1, web:0, cry:0, for:0},
	{rev:2, pwn:0, oth:0, osi:6, ste:0, pro:0, mis:3, web:0, cry:0, for:0}
]

const labelsH = ['DownUnderCTF 2023','vsCTF 2023','MapleCTF 2023','ECW 2023','LakeCTF 2023', 'NewportBlakeCTF 2023'];


//const composedData = ;


/*const chartData = {

};


window.renderChart(chartData, this.container);*/

new Chart(ctxh, {
  type: 'bar',
  data: {
  labels: labelsH,
  datasets: [
    {
      label: 'Reverse',
      xAxisID: 'xAxis1',
      data: datah,
      backgroundColor: '#D741A7',
      parsing: { xAxisKey: 'rev', yAxisKey: 'rev' }
    },
    {
      label: 'Pwn',
      xAxisID: 'xAxis2',
      data: datah,
      backgroundColor: '#892C8D',
      parsing: { xAxisKey: 'pwn', yAxisKey: 'pwn' }
    },
    {
      label: 'Other',
      xAxisID: 'xAxis3',
      data: datah,
      backgroundColor: '#3A1772',
      parsing: { xAxisKey: 'oth', yAxisKey: 'oth' }
    },
    {
      label: 'OSINT',
      xAxisID: 'xAxis4',
      data: datah,
      backgroundColor: '#475898',
      parsing: { xAxisKey: 'osi', yAxisKey: 'osi' }
    },
    {
      label: 'Steg',
      xAxisID: 'xAxis5',
      data: datah,
      backgroundColor: '#5398BE',
      parsing: { xAxisKey: 'ste', yAxisKey: 'ste' }
    },
    {
      label: 'Programming',
      xAxisID: 'xAxis6',
      data: datah,
      backgroundColor: '#7BA6A6',
      parsing: { xAxisKey: 'pro', yAxisKey: 'pro' }
    },
    {
      label: 'Misc',
      xAxisID: 'xAxis7',
      data: datah,
      backgroundColor: '#A3B38E',
      parsing: { xAxisKey: 'mis', yAxisKey: 'mis' }
    },
    {
      label: 'Web',
      xAxisID: 'xAxis8',
      data: datah,
      backgroundColor: '#F2CD5D',
      parsing: { xAxisKey: 'web', yAxisKey: 'web' }
    },
    {
      label: 'Crypto',
      xAxisID: 'xAxis9',
      data: datah,
      backgroundColor: '#E8B954',
      parsing: { xAxisKey: 'cry', yAxisKey: 'cry' }
    },
    {
      label: 'Forensics',
      xAxisID: 'xAxis10',
      data: datah,
      backgroundColor: '#DEA54B',
      parsing: { xAxisKey: 'for', yAxisKey: 'for' }
    }
  ]
},
  options: {
    responsive: true,
    scales: {
      x: {
        stacked: true,
      },
      y: {
        stacked: true
      }
    }
  }
}

</script>