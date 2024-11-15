---
created:
---

---


``` java

// domain

package com.techie.backend.playlist.domain;  
  
import com.techie.backend.user.domain.User;  
import com.techie.backend.video.domain.Video;  
import jakarta.persistence.*;  
import lombok.Builder;  
import lombok.Getter;  
import lombok.NoArgsConstructor;  
  
import java.util.ArrayList;  
import java.util.List;  
  
@NoArgsConstructor  
@Getter  
@Entity  
@Table(name = "playlists")  
public class Playlist {  
  
    @Id  
    @GeneratedValue(strategy = GenerationType.IDENTITY)  
    private Long id;  
  
    @Column(nullable = false)  
    private String name;  
  
    @JoinColumn(name = "user_id", nullable = false)  
    @ManyToOne(fetch = FetchType.LAZY)  
    private User user;  
  
    @OneToMany(mappedBy = "playlist", cascade = CascadeType.ALL, orphanRemoval = true)  
    private List<Video> videos = new ArrayList<>();  
  
    @Builder  
    public Playlist(String name, User user) {  
        this.name = name;  
        this.user = user;  
    }  
  
    public void addVideo(Video video) {  
        videos.add(video);  
        if (!video.getPlaylist().equals(this)) {  
            video.assignPlaylist(this);  
        }  
    }  
}

// dto

package com.techie.backend.playlist.dto;  
  
import lombok.Data;  
  
import java.util.List;  
  
@Data  
public class PlaylistRequest {  
  
    @Data  
    public static class Create {  
        private String name;  
        private List<Long> videoIds;  
    }  
}

package com.techie.backend.playlist.dto;  
  
import com.techie.backend.video.domain.Video;  
import lombok.Data;  
  
import java.util.List;  
  
@Data  
public class PlaylistResponse {  
  
    @Data  
    public static class FindAll {  
        private Long playlistId;  
        private String playlistName;  
        private List<Video> videos;  
    }  
}

//repository

package com.techie.backend.playlist.repository;  
  
import com.techie.backend.playlist.domain.Playlist;  
import org.springframework.data.jpa.repository.JpaRepository;  
import org.springframework.stereotype.Repository;  
  
@Repository  
public interface PlaylistRepository extends JpaRepository<Playlist, Long> {  
  
    Playlist findByUserIdAndId(Long userId, Long playlistId);  
}

package com.techie.backend.playlist.repository;  
  
  
public interface PlaylistRepositoryCustom {  
  
}

package com.techie.backend.playlist.repository;  
  
  
import lombok.RequiredArgsConstructor;  
  
@RequiredArgsConstructor  
public class PlaylistRepositoryImpl implements PlaylistRepositoryCustom {  
  
}

// service

package com.techie.backend.playlist.service;  
  
import com.techie.backend.global.security.UserDetailsCustom;  
import com.techie.backend.playlist.dto.PlaylistRequest;  
import com.techie.backend.playlist.dto.PlaylistResponse;  
import org.springframework.stereotype.Service;  
  
  
@Service  
public interface PlaylistService {  
  
    Boolean createPlaylist(UserDetailsCustom userDetails, PlaylistRequest.Create request);  
  
    PlaylistResponse.FindAll getPlaylist(Long userId, Long playlistId, UserDetailsCustom userDetails);  
}

package com.techie.backend.playlist.service;  
  
  
import com.techie.backend.global.exception.playlist.PlaylistNotFoundException;  
import com.techie.backend.global.exception.user.UserNotFoundException;  
import com.techie.backend.global.security.UserDetailsCustom;  
import com.techie.backend.playlist.domain.Playlist;  
import com.techie.backend.playlist.dto.PlaylistRequest;  
import com.techie.backend.playlist.dto.PlaylistResponse;  
import com.techie.backend.playlist.repository.PlaylistRepository;  
import com.techie.backend.user.domain.User;  
import com.techie.backend.user.repository.UserRepository;  
import com.techie.backend.video.domain.Video;  
import com.techie.backend.video.repository.VideoRepository;  
import lombok.RequiredArgsConstructor;  
import org.springframework.stereotype.Service;  
  
import java.util.List;  
import java.util.stream.Collectors;  
  
@Service  
@RequiredArgsConstructor  
public class PlaylistServiceImpl implements PlaylistService {  
    private final PlaylistRepository playlistRepository;  
    private final VideoRepository videoRepository;  
    private final UserRepository userRepository;  
  
    @Override  
    public Boolean createPlaylist(UserDetailsCustom userDetails, PlaylistRequest.Create request) {  
        User user = userRepository.findByEmail(userDetails.getUsername());  
  
        Playlist playlist = Playlist.builder()  
                .name(request.getName())  
                .user(user)  
                .build();  
        playlistRepository.save(playlist);  
  
        return true;  
    }  
  
    @Override  
    public PlaylistResponse.FindAll getPlaylist(Long userId, Long playlistId, UserDetailsCustom userDetails) {  
        User user = userRepository.findByEmail(userDetails.getUsername());  
  
        if (user == null || !user.getId().equals(userId)) {  
            throw new UserNotFoundException();  
        }  
        Playlist playlist = playlistRepository.findByUserIdAndId(userId, playlistId);  
        if (playlist == null) {  
            throw new PlaylistNotFoundException();  
        }  
        PlaylistResponse.FindAll response = new PlaylistResponse.FindAll();  
  
        response.setPlaylistId(userId);  
        response.setPlaylistName(playlist.getName());  
        response.setVideos(playlist.getVideos());  
        return response;  
    }  
}

// controller

package com.techie.backend.playlist.controller;  
  
  
import com.techie.backend.global.security.UserDetailsCustom;  
import com.techie.backend.playlist.domain.Playlist;  
import com.techie.backend.playlist.dto.PlaylistRequest;  
import com.techie.backend.playlist.dto.PlaylistResponse;  
import com.techie.backend.playlist.service.PlaylistService;  
import com.techie.backend.video.domain.Video;  
import io.swagger.v3.oas.annotations.tags.Tag;  
import lombok.RequiredArgsConstructor;  
import org.springframework.http.ResponseEntity;  
import org.springframework.security.core.annotation.AuthenticationPrincipal;  
import org.springframework.web.bind.annotation.*;  
  
import java.util.List;  
  
@Tag(name = "사용자 재생목록 API", description = "사용자 재생목록 관련 API 엔드포인트")  
@RequestMapping("/api/playlists")  
@CrossOrigin(origins = "http://localhost:3000")  
@RestController  
@RequiredArgsConstructor  
public class PlaylistController {  
    private final PlaylistService playlistService;  
  
    @PostMapping("/")  
    public ResponseEntity<Boolean> createPlaylist(@AuthenticationPrincipal UserDetailsCustom userDetails, @RequestBody PlaylistRequest.Create request) {  
        return ResponseEntity.ok(playlistService.createPlaylist(userDetails, request));  
    }  
  
    @GetMapping("/users/{userId}/playlists/{playlistId}/videos")  
    public ResponseEntity<PlaylistResponse.FindAll> getVideosInPlaylist(  
            @AuthenticationPrincipal UserDetailsCustom userDetails,  
            @PathVariable Long playlistId,  
            @PathVariable Long userId) {  
        PlaylistResponse.FindAll playlistResponse = playlistService.getPlaylist(userId, playlistId, userDetails);  
        return ResponseEntity.ok(playlistResponse);  
    }  
}


```



