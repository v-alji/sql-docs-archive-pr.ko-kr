---
title: 사용자의 사용 권한 테스트(Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: 83a03b85-ea7f-4b4a-b19b-f7eca534ffae
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 8c109eebb4bf06bf7605ca3b7b5930ce18951e41
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651744"
---
# <a name="test-a-user39s-permissions-master-data-services"></a><span data-ttu-id="56e6e-102">사용자의 사용 권한 테스트(Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="56e6e-102">Test a User&#39;s Permissions (Master Data Services)</span></span>
  <span data-ttu-id="56e6e-103">[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]에서 테스트 사용자를 만들고 사용 권한을 테스트하기 위해 웹 애플리케이션에 로그인할 수 있습니다. 사용자가 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] URL에 액세스하려고 시도할 때 사용자의 자격 증명이 인증됩니다.</span><span class="sxs-lookup"><span data-stu-id="56e6e-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], you can create a test user and log into the web application to test permissions.When a user attempts to access the [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] URL, the user's credentials are authenticated.</span></span> <span data-ttu-id="56e6e-104">Internet Explorer의 보안 설정에 따라 인증이 자동으로 진행되는지, 아니면 사용자 이름 및 암호를 입력해야 하는지 여부가 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="56e6e-104">In Internet Explorer, security settings control whether this occurs automatically or if the user must enter a user name and password.</span></span> <span data-ttu-id="56e6e-105">이 설정을 변경하려면 다음 단계를 수행하십시오.</span><span class="sxs-lookup"><span data-stu-id="56e6e-105">To change these settings, complete the following steps:</span></span>  
  
### <a name="to-test-a-users-security"></a><span data-ttu-id="56e6e-106">사용자의 보안을 테스트하려면</span><span class="sxs-lookup"><span data-stu-id="56e6e-106">To test a user's security</span></span>  
  
1.  <span data-ttu-id="56e6e-107">Internet Explorer 7 이상에서 **도구**, **인터넷 옵션**을 차례로 클릭한 다음 **보안** 탭을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="56e6e-107">In Internet Explorer 7 and later, click **Tools**, **Internet Options**, and then click the **Security** tab.</span></span>  
  
2.  <span data-ttu-id="56e6e-108">**로컬 인트라넷** 을 클릭한 다음 **사용자 지정 수준** 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="56e6e-108">Click **Local Intranet** and then the **Custom Level** button.</span></span>  
  
3.  <span data-ttu-id="56e6e-109">**사용자 인증** 섹션에서 **사용자 이름 및 암호 확인**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="56e6e-109">In the **User Authentication** section, choose **Prompt for user name and password**.</span></span>  
  
4.  <span data-ttu-id="56e6e-110">다음에 브라우저 창을 열면 사용자 이름과 암호를 입력하라는 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="56e6e-110">The next time you open the browser window, you will be prompted for a user name and password.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="56e6e-111">참고 항목</span><span class="sxs-lookup"><span data-stu-id="56e6e-111">See Also</span></span>  
 [<span data-ttu-id="56e6e-112">보안&#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="56e6e-112">Security &#40;Master Data Services&#41;</span></span>](security-master-data-services.md)  
  
  
