<script>
  import { onMount } from 'svelte'

  import data1 from 'data/data1.json'
  import data2 from 'data/data2.json'

  let data = []

  onMount(() => {
    const t1 = performance.now()

    console.info("assign start");

    data = data1.slice(0, Math.floor(data1.length / 2))

    const t2 = performance.now()

    console.info('assignment time:', t2 - t1)

    setTimeout(() => {
      const t1 = performance.now()

      console.info("reassign start");

      data = data2

      const t2 = performance.now()

      console.info('reassignment time:', t2 - t1)
    }, 5000)
  })
</script>

<main>
  <table>
    <thead>
      <tr>
        <th>ID</th>
        <th>First name</th>
        <th>Last name</th>
        <th>Email</th>
        <th>Transaction ID</th>
        <th>Merchant ID</th>
        <th>Amount</th>
        <th>Currency</th>
        <th>Date</th>
        <th>Processing Fee</th>
      </tr>
    </thead>
    <tbody>
      {#each data as row (row.transaction_id)}
        <tr>
            <td>{row.id}</td>
            <td>{row.first_name}</td>
            <td>{row.last_name}</td>
            <td>{row.email}</td>
            <td>{row.transaction_id}</td>
            <td>{row.merchant_id}</td>
            <td>{row.amount}</td>
            <td>{row.currency}</td>
            <td>{row.date}</td>
            <td>{row.processing_fee}</td>
        </tr>
      {/each}
    </tbody>
  </table>
</main>

<style>
  :root {
    font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen,
      Ubuntu, Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif;
  }

  main {
    text-align: center;
    padding: 1em;
    margin: 0 auto;
  }
</style>
