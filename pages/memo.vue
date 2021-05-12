<template>
  <section class="container">
    <h1>Memo</h1>
    <table>
      <tr>
        <th>Title</th>
        <td>
          <input type="text" name="title" class="title" size="40" v-model="title" @focus="set_flg">
          <button @click="find">find</button>
        </td>
      </tr>
      <tr>
        <th>Memo</th>
        <td>
          <textarea name="content" class="content" cols="50" rows="5" v-model="content"></textarea>
        </td>
      </tr>
      <tr>
        <th></th>
        <td>
          <button @click="insert">save</button>
          <transition name="del">
            <button v-if="sel_flg != false" @click="remove">delete</button>
          </transition>
        </td>
      </tr>
    </table>
    <hr>
    <ul class="list">
      <li v-for="item in page_items">
        <span @click="select(item)">{{ item.title }}({{item.created}})</span>
      </li>
    </ul>
    <hr>
    <div class="nav">
      <span @click="prev">&lt;prev</span> |
      <span @click="next">next&gt;</span></div>
    </section>
</template>