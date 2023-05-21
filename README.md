private void FilterData2()
{
    string query = "SELECT id, name, stage, group_time, group_type, late_point FROM mydb WHERE 1=1";

    if (!string.IsNullOrEmpty(txt_id.Text))
    {
        query += " AND id LIKE '%' + @id + '%'";
        cmd.Parameters.AddWithValue("@id", txt_id.Text);
    }
    if (box_stage.SelectedItem != null)
    {
        query += " AND stage LIKE '%' + @stage + '%'";
        cmd.Parameters.AddWithValue("@stage", box_stage.SelectedItem.ToString());
    }
    if (box_grouptime.SelectedItem != null)
    {
        query += " AND group_time LIKE '%' + @group_time + '%'";
        cmd.Parameters.AddWithValue("@group_time", box_grouptime.SelectedItem.ToString());
    }
    if (box_grouptype.SelectedItem != null)
    {
        query += " AND group_type LIKE '%' + @group_type + '%'";
        cmd.Parameters.AddWithValue("@group_type", box_grouptype.SelectedItem.ToString());
    }

    cmd.CommandText = query;
    cmd.Parameters.Clear(); // Clear the parameters of the SqlCommand
    SqlDataAdapter adapter = new SqlDataAdapter(cmd);
    DataTable dt = new DataTable();
    adapter.Fill(dt);
    dataGridView1.DataSource = dt;

    countingnames();
}
