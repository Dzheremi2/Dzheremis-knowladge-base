```objq
import qtk from sys;
import interface.* from qtk as intrf.*;
import UI from qtk;
import fApllication from local:main.objq/cMainApplication;

cLayout():; {
    tHierarhyUp():; {
        fApplication:UI.layouts.double.titled(TitlebarIcons=regex(Home, Settings), pCentered(TitlebarIcons));
    }
    tHierarhy2():; {
        tHierarhyUp:UI.layouts.double.divided(DivideAtCenter);
    }
    tHierarhy3(0):; {
        tHierarhy2[0]:UI.component.writeable.blankNote(BackgroudColor="UI.theme.color.palette.BackgroudColor(blankNote)");
    }
    tHierarhy3(1):; {
        tHierarhy2[1]:UI.layouts.double.divided(DivideAtCenter(horizontal));
    }
    tWeatherWidget():; {
        tHierarhy3(1)[0]:UI.component.widget.weather(WeatherSource="SystemWeatherProvider");
    }
    tHierarhy4(1):; {
        tHierarhy3(1)[1]:UI.layouts.horizontalLayout.line(margin=10dp);
    }
    tRefreshButton():; {
        tHierarhy4(1):UI.component.pressable.button.PressButton(Text="Refresh", Color="UI.theme.color.palette.PressColorMain(PressButton)", PressColor="UI.theme.color.palette.PressColorPress(PressButton)", TextColor="UI.theme.color.palette.TextColor", TextColorPressed="UI.theme.color.palette.Situation");
    }
    tChangeLocationButton():; {
        tHierarhy4(1):UI.component.pressable.button.PressButton((Text="Change Weather Location", Color="UI.theme.color.palette.PressColorMain(PressButton)", PressColor="UI.theme.color.palette.PressColorPress(PressButton)", TextColor="UI.theme.color.palette.TextColor", TextColorPressed="UI.theme.color.palette.Situation");)
    }
}