#Queryparametr
http://www.contoso.com/pizzas/margherita?extratopping=pineapple.

var uri = NavManager.ToAbsoluteUri(NavManager.Uri);
if (QueryHelpers.ParseQuery(uri.Query).TryGetValue("extratopping", out var extraTopping))
{
			ToppingName = System.Convert.ToString(extraTopping);
}


#FormValidation

<EditForm Model="@shirt" OnSubmit="ValidateData">
    <!-- Omitted for brevity -->
    <input type="submit" class="btn btn-primary" value="Save"/>
    <p></p>
    <div>@Message</div>
</EditForm>

@code {
    private string Message = String.Empty;

    // Omitted for brevity

    private async Task ValidateData(EditContext editContext)
    {
        if (editContext.Model is not Shirt shirt)
        {
            Message = "T-Shirt object is invalid";
            return;
        }

        if (shirt is { Color: ShirtColor.Red, Size: ShirtSize.ExtraLarge })
        {
            Message = "Red T-Shirts not available in Extra Large size";
            return;
        }


#InputRadioGroup

         <InputRadioGroup Name="color" @bind-Value=shirt.Color>
            @foreach(var shirtColor in Enum.GetValues(typeof(ShirtColor)))
            {
                <label>@shirtColor:
                    <InputRadio Name="color" Value="@shirtColor"></InputRadio>
                </label>
                <br />
            }