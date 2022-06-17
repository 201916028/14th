# 비디오 재생 앱이란?
비디오 플레이어는 아이폰 사용자들이 가장 많이 사용하는 앱 중의 하나입니다. 등하굣길이나 출퇴근길에 영화를 감상하거나 동영상 강좌를 듣는 사용자들을 쉽게 볼 수 있습니다. 아이폰에서의 비디오 재생 방법을
잘 활용되면 다음과 같은 비디오 재생 앱도 만들 수 있습니다.

# 소스코드
import UIKit
import AVKit

class ViewController: UIViewController {

    override func viewDidLoad() {
        super.viewDidLoad()
        // Do any additional setup after loading the view.
    }

    @IBAction func btnPlayInternalMovie(_ sender: UIButton) {
    // 비디오 파일명을 사용하여 비디오가 저장된 앱 내부의 파일 경로를 받아옴
    
        // 내부 파일 mp4
        let filePath:String? = Bundle.main.path(forResource: "FastTyping", ofType: "mp4")
        // 앱 내부의 파일명을 NSURL 형식으로 변경
        let url = NSURL(fileURLWithPath: filePath!)

        playVideo(url: url) // 앞에서 얻은 url을 사용하여 비디오를 재생
    }
    
    @IBAction func btnPlayerExternalMovie(_ sender: UIButton) {
        // 외부 파일 mp4
        let url = NSURL(string: "https://dl.dropboxusercontent.com/s/e38auz050w2mvud/Fireworks.mp4")!

        playVideo(url: url) // 앞에서 얻은 url을 사용하여 비디오를 재생
    }
    
    private func playVideo(url: NSURL)  {
    // AVPlayerViewController의 인스턴스를 생성
        let playerController = AVPlayerViewController()
        
        //비디오 URL로 초기화된 AVPlayer의 인스턴스를 생성
        let player = AVPlayer(url: url as URL)
        playerController.player = player
        
        self.present(playerController, animated: true) {
            player.play() // 비디오 재생
        }
    }
}
