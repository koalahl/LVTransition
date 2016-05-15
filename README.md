# LVTransition
A transition lib in swift .


###Usage
1.For Present/Dismiss
```objc
class ViewController: UIViewController ,ViewControllerTransitionable{

var lv_transition:LVTransition?//协议中声明的属性

override func viewDidLoad() {
super.viewDidLoad()
// Do any additional setup after loading the view, typically from a nib.

self.title = "First VC"

}

override func didReceiveMemoryWarning() {
super.didReceiveMemoryWarning()
// Dispose of any resources that can be recreated.
}

@IBAction func presentVC(sender: AnyObject) {

let secondVC = UIStoryboard(name: "Main", bundle: nil).instantiateViewControllerWithIdentifier("SecondViewController")

self.lv_persent(secondVC, animationMode: .Fade, completion: nil)

}

}
```

2.For Push/Pop

```objc
class PushViewController: UIViewController ,NavigationTransitionable{

@IBOutlet weak var imageView: UIImageView!

var lv_pushTransition: LVTransition?

var animator :LVTransitionAnimator?

override func viewDidLoad() {
super.viewDidLoad()
self.view.backgroundColor = UIColor.whiteColor()
// Do any additional setup after loading the view.
self.imageView.addGestureRecognizer(UITapGestureRecognizer(target: self, action: #selector(PushViewController.pushTo)))
}

func pushTo() {
let popVC = PopViewController()

//self.lv_push(popVC, animationMode: LVAnimatorMode.Move(keyView: self.imageView), completion: nil)
self.lv_push(popVC, animationMode: LVAnimatorMode.Move(keyView: self.imageView, toRect: CGRectMake(20, 90, 80, 80)), completion: nil)
}

override func didReceiveMemoryWarning() {
super.didReceiveMemoryWarning()
// Dispose of any resources that can be recreated.
}


}
```