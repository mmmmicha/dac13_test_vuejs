<template>
    <div>
        <h1>Welcome to {{title}}!</h1>
        <input type="text" v-model="input1" />
        <button type="button" @click="getData">Get</button>
        <button type="button" @click="setData">Set</button>

        <select class="form-control" v-model="region" @change="changeRegion">
            <!-- :을 쓰게되면 script에 명시해놓은 데이터들을 직접접근하여 사용할 수 있다. -->
            <option :key="i" :value="d.v" v-for="(d,i) in options">{{d.t}}</option>
        </select>
        <!-- v-if 와 v-show 의 차이 ; show는 렌더링은 하지만 보이고 안보이고 차이 ; if는 렌더링 자체를 안해버림 -->
        <!-- v-show 가 리소스 소모가 적음 ; but 용도는 분명 장단점이 있음 -->
        <table class="table table-bordered" v-if="tableShow" v-show="tableShow">
            <tr :key="i" v-for="(d,i) in options">
                <td>{{d.v}}</td>
                <td>{{d.t}}</td>
            </tr>
        </table>
    </div>
</template>
<script>
export default {
    data() {
        return {
            title: "dac13 테스트",
            title2: "테스트2",
            input1: "동적할당가능하네?",
            options: [
                {v:"s", t:"서울"},
                {v:"j", t:"제주"},
                {v:"b", t:"부산"}
            ],
            region: "j",
            tableShow: true,
        };
    },
    watch: {
        // 해당 명의 컴포넌트의 조금이라도 변경이 일어날경우
        input1() {
            console.log(this.input1);
        }
    },
    methods: {
        getData() {
            alert(this.input1)
        },
        setData() {
            this.input1 = "12345";
        },
        changeRegion() {
            alert(this.region);
        }
    },
    // lifecycle
    beforeCreate() {
        console.log("beforeCreate");
    },
    created() {
        console.log("created");
    },
    beforeMount() {
        console.log("beforeMount");
    },
    mounted() {
        console.log("mounted");
    },
    beforeUpdate() {
        console.log("beforeUpdate");
    },
    updated() {
        console.log("updated");
    },
    beforeDestroy() {
        console.log("beforeDestroy");
    },
    destroyed() {
        console.log("destroyed");
    }
}
</script>