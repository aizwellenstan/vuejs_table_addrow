<template>
  <div id="app" class="container">
    <table class="table table-striped">
        <thead>
            <tr>
                <th>Object</th>
                <th>Value</th>
                <th>Day</th>
                <th>H</th>
                <th>M</th>
                <th></th>
            </tr>
        </thead>
        <tbody>
            <!-- 各要素を表示 -->
            <tr v-for="(elem, index) in elements" :key='index'>
                <td>{{ elem.object }}</td>
                <td>{{ elem.value }}</td>
                <td>{{ elem.day }}</td>
                <td>{{ elem.hour }}</td>
                <td>{{ elem.minute }}</td>
                <!-- クリックして要素を削除 -->
                <td><span v-on:click="remove(index)" class="glyphicon glyphicon-remove"></span></td>
            </tr>
            <!-- 新しい要素を追加するための行 -->
            <tr>
                <td>
                    <select id="new-object" type="text">
                        <option>A</option>
                        <option>B</option>
                    </select>
                </td>
                <td>
                    <input id="new-value" type="text">
                </td>
                <td>
                    <select id="new-day" type="text">
                        <option>Mon</option>
                        <option>Tue</option>
                        <option>Wed</option>
                        <option>Thu</option>
                        <option>Fri</option>
                    </select>
                </td>
                <td>
                    <input id="new-hour" type="text">
                </td>
                <td>
                    <input id="new-minute" type="text">
                </td>
                <!-- クリックして要素を追加 -->
                <td>
                    <span v-on:click="append" class="glyphicon glyphicon-plus"></span>
                </td>
            </tr>
        </tbody>
    </table>
    <button>Submmit</button>
</div>
</template>

<script>
export default {
  data() {
     return{
         elements: []
     }
},
    methods: {
        // 要素を追加
        append: function() {
            this.elements.push({
                object: $('#new-object').val(),
                value: $('#new-value').val(),
                day: $('#new-day').val(),
                hour: $('#new-hour').val(),
                minute: $('#new-minute').val(),
            });
            // テキストボックスの中身を空に
            $('#new-object').val('');
            $('#new-value').val('');
            $('#new-day').val('');
            $('#new-hour').val('');
            $('#new-minute').val('');
        },
        // 要素を削除
        remove: function(index) {
            this.elements.splice(index, 1);
        }
    }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
 
</style>
