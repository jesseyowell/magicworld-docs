---
title: Tables n Stuff
excerpt: ''
deprecated: false
hidden: false
metadata:
  title: ''
  description: ''
  robots: index
next:
  description: ''
---
<Table align={["left","left","left"]}>
  <thead>
    <tr>
      <th style={{ textAlign: "left" }}>
        Item 1
      </th>

      <th style={{ textAlign: "left" }}>
        Item 2
      </th>

      <th style={{ textAlign: "left" }}>
        Item 3
      </th>
    </tr>
  </thead>

  <tbody>
    <tr>
      <td style={{ textAlign: "left" }}>
        <ul>   
          <li>Cheese</li>   
          <li>Beans</li>   
          <li>Lettuce</li> 
        </ul>
      </td>

      <td style={{ textAlign: "left" }}>

      </td>

      <td style={{ textAlign: "left" }}>

      </td>
    </tr>

    <tr>
      <td style={{ textAlign: "left" }}>

      </td>

      <td style={{ textAlign: "left" }}>

      </td>

      <td style={{ textAlign: "left" }}>

      </td>
    </tr>
  </tbody>
</Table>

<HTMLBlock>{`
<style>
li {
  margin: 10px 0;
}
</style>
`}</HTMLBlock>