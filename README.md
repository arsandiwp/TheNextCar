# THE NEXT CAR APPS
The Next Car adalah sebuah contoh project MVC yang dibuat dengan tujuan pada keamanan saat mengendarai mobil.

## Scope of Functionalities
- Apa kegunaan DoorController.cs?
- Apa kegunaan Model Door.cs?
- Apa kegunaan Interface OnDoorChanged ? 

### DoorController.cs ?
- DoorController berfungsi untuk mengetahui apakah udah terLock atau belum pintu dari mobil itu.

```csharp
    namespace TheNextCar.Controller
{
    class DoorController
    {
        private Door door;
        private OnDoorChanged onDoorChanged;

        public DoorController(OnDoorChanged onDoorChanged)
        {
            this.door = new Door();
            this.onDoorChanged = onDoorChanged;
        }
```

### Door.cs ?
- Door.cs berfungsi untuk mengetahui fungsi door Closed atau Locked.
```csharp
    namespace TheNextCar.Model
{
    class Door
    {
        private bool closed;
        private bool locked;
```


### OnDoorChanged ?
- OnDoorChanged berfungsi untuk mengganti fungsi dari Door dan DoorController.

```csharp
    public DoorController(OnDoorChanged onDoorChanged)
        {
            this.door = new Door();
            this.onDoorChanged = onDoorChanged;
        }

        public void close()
        {
            this.door.close();
            this.onDoorChanged.doorStatusChanged("CLOSED", "Door is Closed");
        }

        public void open()
        {
            this.door.open();
            this.onDoorChanged.doorStatusChanged("OPENED", "Door is Opened");
        }

        public void activateLock()
        {
            if (this.door.isClosed())
            {
                this.door.activateLock();
                onDoorChanged.doorSecurityChanged("LOCKED", "Door Locked");
            }
            else
            {
                unlock();
            }
        }
```
 
