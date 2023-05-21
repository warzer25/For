private void reset_CheckedChanged(object sender, EventArgs e)
{
    box_stage.SelectedItem = null;
    box_grouptype.SelectedItem = null;
    box_grouptime.SelectedItem = null;
    box_class.SelectedItem = null;
    box_sub.SelectedItem = null;

    DisplayData();
    DisplayData2();
    countingnames();

    reset.Checked = false;
}
