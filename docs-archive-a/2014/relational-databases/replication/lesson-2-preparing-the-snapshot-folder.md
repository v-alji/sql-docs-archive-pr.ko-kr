---
title: '2단원: 스냅샷 폴더 준비 | Microsoft 문서'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- replication [SQL Server], tutorials
ms.assetid: f286cde9-c0d0-43ef-b7ba-53c3cbb8906c
author: rothja
ms.author: jroth
ms.openlocfilehash: 5d98c7433d0bd50504f20f7f576fcf0b20154c81
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87739711"
---
# <a name="lesson-2-preparing-the-snapshot-folder"></a><span data-ttu-id="df683-102">2단원: 스냅샷 폴더 준비</span><span class="sxs-lookup"><span data-stu-id="df683-102">Lesson 2: Preparing the Snapshot Folder</span></span>
  <span data-ttu-id="df683-103">이 단원에서는 게시 스냅샷을 만들고 저장하는 데 사용되는 스냅샷 폴더를 구성하는 방법을 배웁니다.</span><span class="sxs-lookup"><span data-stu-id="df683-103">In this lesson, you will learn to configure the snapshot folder that is used to create and store the publication snapshot.</span></span>  
  
### <a name="to-create-a-share-for-the-snapshot-folder-and-assign-permissions"></a><span data-ttu-id="df683-104">스냅샷 폴더에 대한 공유를 만들고 사용 권한을 할당하려면</span><span class="sxs-lookup"><span data-stu-id="df683-104">To create a share for the snapshot folder and assign permissions</span></span>  
  
1.  <span data-ttu-id="df683-105">Windows 탐색기에서 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터 폴더로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="df683-105">In Windows Explorer, navigate to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data folder.</span></span> <span data-ttu-id="df683-106">기본 위치는 C:\Program Files\Microsoft SQL Server\MSSQL.X\MSSQL\Data입니다.</span><span class="sxs-lookup"><span data-stu-id="df683-106">The default location is C:\Program Files\Microsoft SQL Server\MSSQL.X\MSSQL\Data.</span></span>  
  
2.  <span data-ttu-id="df683-107">**repldata**라는 새 폴더를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="df683-107">Create a new folder named **repldata**.</span></span>  
  
3.  <span data-ttu-id="df683-108">이 폴더를 마우스 오른쪽 단추로 클릭한 다음 **속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="df683-108">Right-click this folder and click **Properties**.</span></span>  
  
4.  <span data-ttu-id="df683-109">**repldata 속성** 대화 상자의 **공유** 탭에서 **공유**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="df683-109">On the **Sharing** tab in the **repldata Properties** dialog box, click **Share**.</span></span>  
  
5.  <span data-ttu-id="df683-110">**파일 공유** 대화 상자에서 **공유**를 클릭한 다음 **완료**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="df683-110">In the **File Sharing** dialog box, click **Share**, and then click **Done**.</span></span>  
  
6.  <span data-ttu-id="df683-111">**보안** 탭에서 **편집**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="df683-111">On the **Security** tab, click **Edit**.</span></span>  
  
7.  <span data-ttu-id="df683-112">**권한** 대화 상자에서 **추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="df683-112">In the **Permissions** dialog box, click **Add.**</span></span> <span data-ttu-id="df683-113">**사용자, 컴퓨터, 서비스 계정 또는 그룹 선택** 입력란에 1 단원에서 만든 스냅숏 에이전트 계정의 이름을 \<_Machine_Name> _**\ repl_snapshot**입력 합니다 \<*Machine_Name> . 여기서 \*은 게시자의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="df683-113">In the **Select User, Computers, Service Account, or Groups** text box, type the name of the Snapshot Agent account created in Lesson 1, as \<_Machine_Name>_**\repl_snapshot**, where \<*Machine_Name>\* is the name of the Publisher.</span></span> <span data-ttu-id="df683-114">**이름 확인**을 클릭한 다음 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="df683-114">Click **Check Names**, and then click **OK**.</span></span>  
  
8.  <span data-ttu-id="df683-115">이전 단계를 반복 하 여 배포 에이전트, \<_Machine_Name> _ **\ repl_distribution**및 \<_Machine_Name> 병합 에이전트 _에 대 한 권한을 **\ repl_merge**로 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="df683-115">Repeat the previous step to add permissions for the Distribution Agent, as \<_Machine_Name>_**\repl_distribution**, and for the Merge Agent as \<_Machine_Name>_**\repl_merge**.</span></span>  
  
9. <span data-ttu-id="df683-116">다음 사용 권한이 허용되는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="df683-116">Verify the following permissions are allowed:</span></span>  
  
    -   <span data-ttu-id="df683-117">repl_snapshot - 모든 권한</span><span class="sxs-lookup"><span data-stu-id="df683-117">repl_snapshot - Full Control</span></span>  
  
    -   <span data-ttu-id="df683-118">repl_distribution - 읽기</span><span class="sxs-lookup"><span data-stu-id="df683-118">repl_distribution - Read</span></span>  
  
    -   <span data-ttu-id="df683-119">repl_merge - 읽기</span><span class="sxs-lookup"><span data-stu-id="df683-119">repl_merge - Read</span></span>  
  
10. <span data-ttu-id="df683-120">**확인** 을 클릭하여 **repldata 속성** 대화 상자를 닫고 repldata 공유를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="df683-120">Click **OK** to close the **repldata Properties** dialog box and create the repldata share.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="df683-121">다음 단계</span><span class="sxs-lookup"><span data-stu-id="df683-121">Next Steps</span></span>  
 <span data-ttu-id="df683-122">스냅샷 폴더에 대한 공유를 성공적으로 구성했습니다.</span><span class="sxs-lookup"><span data-stu-id="df683-122">You have successfully configured the share for the snapshot folder.</span></span> <span data-ttu-id="df683-123">다음 단원에서는 배포를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="df683-123">Next, you will configure distribution.</span></span> <span data-ttu-id="df683-124">[3단원: 배포 구성](lesson-3-configuring-distribution.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="df683-124">See [Lesson 3: Configuring Distribution](lesson-3-configuring-distribution.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="df683-125">참고 항목</span><span class="sxs-lookup"><span data-stu-id="df683-125">See Also</span></span>  
 [<span data-ttu-id="df683-126">스냅샷 폴더 보안 설정</span><span class="sxs-lookup"><span data-stu-id="df683-126">Secure the Snapshot Folder</span></span>](security/secure-the-snapshot-folder.md)  
  
  
