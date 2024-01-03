 @GetMapping("/detail/{profileName}") // @AuthenticationPrincipal //
    public String profileDetail(Model model, Principal principal, @PathVariable("profileName")String profileName) { //@RequestParam(name = "postid", required = false) Long postid

        Profile targetProfile = profileService.getProfileByName(profileName);
        List<Post> postList = postService.getPostsbyAuthor(targetProfile);
        List<Profile> followers = followingMapService.getMyfollowers(targetProfile);
        List<Profile> followings = followingMapService.getMyfollowings(targetProfile);

        model.addAttribute("profile", targetProfile);
        model.addAttribute("postList", postList);
        model.addAttribute("followers", followers);
        model.addAttribute("followings", followings);


//        ProfileDto dto = null;
////        Post thispost = postService.getPost(postid);
//
//        if (principal == null) { //postid ㅇ (null일수가 없음) //게시글에서 작성자 플필 클릭한거
////            dto = profileService.getProfileDtoByNotLogined(thispost);
//            model.addAttribute("profileDto", dto);
//            return "Profile/profile_detail";
//        }
//
//        if (postid == null) { //principal ㅇ, postid X
////            dto = profileService.getProfileDtoByLoginId(principal.getName());
//            model.addAttribute("profileDto", dto);
//            return "Profile/profile_detail";
//        }
//
////        dto = profileService.getProfileDtoByLoginId(thispost.getAuthor().getProfileName());
////        model.addAttribute("profileDto", dto);
////        return "Profile/profile_detail";

        return "Profile/profile_detail";
    }
