<script>
import axios from 'axios';

const API = 'http://localhost:3000';

export default {
  async get() {
    const data = await axios.get(`${API}/projects`);
    return data.data;
  },
};
</script>
