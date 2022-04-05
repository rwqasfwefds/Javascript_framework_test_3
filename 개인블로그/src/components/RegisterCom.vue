<template>
    <div>
        <h1>회원가입</h1>
        <div>
            <form>
                <fieldset>
                    <table>
                        <tr>
                            <td>아이디</td>
                            <td><input type="text" required v-model="id" /></td>
                        </tr>
                        <tr>
                            <td>비밀번호</td>
                            <td>
                                <input
                                    type="password"
                                    required
                                    v-model="password"
                                />
                            </td>
                        </tr>
                        <tr>
                            <td>이름</td>
                            <td>
                                <input type="text" required v-model="name" />
                            </td>
                        </tr>
                        <tr>
                            <td>전화번호</td>
                            <td>
                                <input
                                    type="number"
                                    required
                                    v-model="phonenumber"
                                />
                            </td>
                        </tr>
                        <tr>
                            <td>생년월일</td>
                            <td><input id="datepicker" v-model="birth" /></td>
                        </tr>
                        <tr>
                            <td>이메일</td>
                            <td>
                                <input
                                    type="text"
                                    placeholder="abcd@naver.com"
                                    v-model="email"
                                />
                            </td>
                        </tr>

                        <tr>
                            <td></td>
                            <td>
                                <input
                                    type="submit"
                                    value="가입"
                                    v-model="submitted"
                                />
                            </td>
                        </tr>
                    </table>
                </fieldset>
                <button><router-link to="/">되돌아가기</router-link></button>
            </form>
        </div>
        <div></div>
    </div>
</template>

<script>
export default {
    data() {
        return {
            id: "",
            password: "",
            name: "",
            phonenumber: "",
            birth: "",
            email: "",
            submitted: "가입",
        };
    },
};
</script>

<style lang="scss" scoped>
@import "../assets/css/register_member.scss";
</style>
