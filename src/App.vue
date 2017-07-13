<template>
    <div class="container">
        <div class="row">
            <div class="col-xs-12">
                <h1>Add Blog Post</h1>

                <form>
                    <div class="form-group">
                        <label for="title">Title</label>
                        <input type="text" class="form-control" id="title" v-model.trim="post.title">
                    </div>

                    <div class="form-group">
                        <label for="content">Content</label>
                        <textarea class="form-control" id="content" v-model.lazy.trim="post.content" cols="30" rows="10"></textarea>
                    </div>

                    <div class="form-group">
                        <input type="checkbox" id="publish-immediately" v-model="post.publishImmediately">
                        <label for="publish-immediately">Publish immediately</label>
                    </div>

                    <div class="form-group">
                        <label>Share on</label>

                        <div v-for="media in formData.socialMedia">
                            <input type="checkbox" :id="media" :value="media" v-model="post.shareOn">
                            <label :for="media">{{ media }}</label>
                        </div>
                    </div>

                    <div class="form-group">
                        <label>Category</label>

                        <div v-for="category in formData.categories">
                            <input type="radio" :id="category" :value="category" v-model="post.category">
                            <label :for="category">{{ category }}</label>
                        </div>
                    </div>

                    <div class="form-group">
                        <label for="select-series">Series</label>

                        <select class="form-control" id="select-series" v-model="post.series">
                            <option value="">Choose Series</option>
                            <option v-for="series in formData.series" :value="series">{{ series }}</option>
                        </select>
                    </div>
                </form>

                <hr>

                <table class="table table-striped">
                    <thead>
                        <tr>
                            <td class="col-xs-6"><strong>Field</strong></td>
                            <td class="col-xs-6"><strong>Value</strong></td>
                        </tr>
                    </thead>
                    <tbody>
                        <tr>
                            <td>Title</td>
                            <td>{{ post.title }}</td>
                        </tr>
                        <tr>
                            <td>Content</td>
                            <td style="white-space: pre;">{{ post.content }}</td>
                        </tr>
                        <tr>
                            <td>Publish immediately</td>
                            <td>{{ post.publishImmediately }}</td>
                        </tr>
                        <tr>
                            <td>Share on</td>
                            <td>
                                <ul>
                                    <li v-for="media in post.shareOn">{{ media }}</li>
                                </ul>
                            </td>
                        </tr>
                        <tr>
                            <td>Category</td>
                            <td>{{ post.category }}</td>
                        </tr>
                        <tr>
                            <td>Series</td>
                            <td>{{ post.series }}</td>
                        </tr>
                    </tbody>
                </table>
            </div>
        </div>
    </div>
</template>

<script>
    export default {
        data() {
            return {
                post: {
                    title: '',
                    content: '',
                    publishImmediately: true,
                    shareOn: ['Facebook'],
                    category: 'Backend',
                    series: 'Complete Guide to Elasticsearch'
                },
                formData: {
                    socialMedia: ['Facebook', 'Twitter'],
                    categories: ['Frontend', 'Backend'],
                    series: [
                        'Vue.js: From Beginner to Professional',
                        'Complete Guide to Elasticsearch'
                    ]
                }
            };
        }
    }
</script>

<style>
    input[type="radio"] + label,
    input[type="checkbox"] + label {
        font-weight: normal;
    }
</style>