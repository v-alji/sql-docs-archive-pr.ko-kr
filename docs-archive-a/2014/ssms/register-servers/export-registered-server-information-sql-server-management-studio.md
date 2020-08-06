---
title: 등록된 서버 정보 내보내기
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql12.swb.exportregisteredservers.f1
helpviewer_keywords:
- Registered Servers [SQL Server], exporting
- exporting registered server information
- transferring registered server information
ms.assetid: b65e168f-b6bf-489c-b8ad-3b8644acf0b6
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 03092de2d722e8f8b807dbb3d23c4b4e2b91f6f8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87737401"
---
# <a name="export-registered-server-information-sql-server-management-studio"></a><span data-ttu-id="73114-102">등록된 서버 정보 내보내기(SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="73114-102">Export Registered Server Information (SQL Server Management Studio)</span></span>
  <span data-ttu-id="73114-103">이 항목에서는 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]에서 등록된 서버 정보를 저장하여 내보내고 그 정보를 다른 사용자나 서버로 배포하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="73114-103">This topic describes how to save and export registered server information in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]and distribute it to other employees or servers.</span></span> <span data-ttu-id="73114-104">이러한 내보내기 기능을 사용하면 여러 대의 컴퓨터에서 일관된 사용자 인터페이스를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="73114-104">You can use this export feature to present a consistent user interface on multiple computers.</span></span>  
  
 <span data-ttu-id="73114-105">등록된 서버 파일을 내보냈다가 다시 가져오면 등록된 서버에 있는 동일한 서버로 여러 컴퓨터를 쉽게 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="73114-105">Exporting and then importing Registered Server files lets you easily configure several computers with the same servers in Registered Servers.</span></span> <span data-ttu-id="73114-106">이 작업은 여러 곳에 위치한 컴퓨터에서 다수의 서버를 관리할 때나 경험이 적은 사용자를 위해 기본 연결 설정을 구성하려는 경우에 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="73114-106">This is useful when managing a large number of servers from computers in several locations, or when you want to configure a less experienced user with basic connection settings.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="73114-107">SQL Server 인증을 사용하는 서버 등록은 사용자 단위로 암호를 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="73114-107">Server registrations that use SQL Server Authentication store passwords on a per-user basis.</span></span> <span data-ttu-id="73114-108">서버 등록을 내보냈다가 가져온 후 사용자는 처음으로 연결할 때 각 서버의 암호를 입력하여 등록된 서버 목록에 암호를 저장해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="73114-108">After exporting and importing the server registrations, users must enter the password for each server the first time they connect, storing the passwords in their lists of registered servers.</span></span> <span data-ttu-id="73114-109">Windows 인증을 통해 등록된 서버에는 이 작업이 필요하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="73114-109">This is not necessary for servers registered using Windows Authentication.</span></span>  
  
##  <a name="SSMSProcedure"></a>  
  
#### <a name="to-export-registered-server-information"></a><span data-ttu-id="73114-110">등록된 서버 정보를 내보내려면</span><span class="sxs-lookup"><span data-stu-id="73114-110">To export registered server information</span></span>  
  
1.  <span data-ttu-id="73114-111">등록된 서버에서 서버 그룹을 마우스 오른쪽 단추로 클릭한 다음 **내보내기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="73114-111">In Registered Servers, right-click a server group, and then click **Export**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="73114-112">개별 서버, 등록된 모든 서버 트리 또는 등록된 서버 트리의 하위 집합을 내보낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="73114-112">You can export an individual server, all of the registered server tree, or a subset of the registered server tree.</span></span>  
  
2.  <span data-ttu-id="73114-113">**등록된 서버 내보내기** 대화 상자에서 다음과 같이 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="73114-113">In the **Export Registered Servers** dialog box, make the following selections.</span></span>  
  
     <span data-ttu-id="73114-114">**서버 그룹**</span><span class="sxs-lookup"><span data-stu-id="73114-114">**Server group**</span></span>  
     <span data-ttu-id="73114-115">내보낼 서버 그룹을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="73114-115">Specify the server group which will be exported.</span></span> <span data-ttu-id="73114-116">등록된 모든 서버, 특정 서버 그룹에 속한 등록된 서버 또는 등록된 단일 서버를 내보내기 파일로 내보냅니다.</span><span class="sxs-lookup"><span data-stu-id="73114-116">Export all registered servers, registered servers in a particular server group, or a single registered server to the export file.</span></span> <span data-ttu-id="73114-117">내보내기 기능은 재귀적입니다. 예를 들어 서버 그룹 A에는 서버 그룹 B가, 서버 그룹 B에는 서버 그룹 C와 D가 포함된 경우 서버 그룹 A를 내보내면 A, B, C, D의 모든 항목이 내보내집니다.</span><span class="sxs-lookup"><span data-stu-id="73114-117">The export functionality is recursive; for example, if server group A contains server group B, and server group B contains server groups C and D, exporting server group A exports all entries in A, B, C, and D.</span></span>  
  
     <span data-ttu-id="73114-118">서버 그룹은 현재 등록된 서버 트리의 서버 그룹만 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="73114-118">The server group displays only the server groups of the current registered server tree.</span></span>  
  
     <span data-ttu-id="73114-119">**내보낼 파일**</span><span class="sxs-lookup"><span data-stu-id="73114-119">**Export file**</span></span>  
     <span data-ttu-id="73114-120">입력란에 내보낼 파일 이름을 입력하거나 찾아보기 단추( **...** )를 사용하여 클라이언트 컴퓨터에서 내보낼 파일을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="73114-120">Type the name of the export file in the text box or use the Browse button (**...**) to locate an export file on the client computer.</span></span> <span data-ttu-id="73114-121">기존 파일을 선택하면 등록된 서버 정보가 파일에 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="73114-121">If you select an existing file, the registered server information is appended to the file.</span></span> <span data-ttu-id="73114-122">.regsrvr 확장명을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="73114-122">Use the .regsrvr extension.</span></span> <span data-ttu-id="73114-123">등록된 서버 정보를 다른 사용자나 컴퓨터도 사용할 수 있게 하려면 네트워크에 해당 파일을 저장하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="73114-123">If you want your registered server information to be available to other users or another computer, you can save the file on the network.</span></span> <span data-ttu-id="73114-124">다른 사용자는 해당 파일에 액세스하여 등록된 서버 정보의 일부 또는 전체를 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="73114-124">Other users can access the file and import part or all of the registered server information.</span></span> <span data-ttu-id="73114-125">파일을 내보낼 때 기존 파일을 선택하면 파일 내용을 새 서버 등록 정보로 덮어씁니다.</span><span class="sxs-lookup"><span data-stu-id="73114-125">If you select an existing file as your export file, the contents of the file are overwritten with the server registration information.</span></span>  
  
     <span data-ttu-id="73114-126">**파일 내보내기에 사용자 이름 및 암호 포함 안 함**</span><span class="sxs-lookup"><span data-stu-id="73114-126">**Do not include user names and passwords in the export file**</span></span>  
     <span data-ttu-id="73114-127">파일을 내보낼 때 사용자 이름을 제외합니다.</span><span class="sxs-lookup"><span data-stu-id="73114-127">Exclude user names when exporting the file.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="73114-128">내보낼 파일이 암호화되더라도 파일에 사용자 이름과 SQL Server 인증 암호가 포함되면 파일에 대한 액세스를 신중하게 제어해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="73114-128">Although the export files are encrypted, if user names and SQL Server Authentication passwords are included in the file, access to the file should be carefully controlled.</span></span> <span data-ttu-id="73114-129">따라서 사용자 이름과 암호는 기본적으로 내보낼 파일에서 제외됩니다.</span><span class="sxs-lookup"><span data-stu-id="73114-129">User names and passwords are therefore excluded from the export file by default.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73114-130">참고 항목</span><span class="sxs-lookup"><span data-stu-id="73114-130">See Also</span></span>  
 <span data-ttu-id="73114-131">[등록 된 서버 정보 가져오기 &#40;SQL Server Management Studio&#41;](import-registered-server-information-sql-server-management-studio.md) [등록 된 새 서버 &#40;SQL Server Management Studio를 만듭니다&#41;](create-a-new-registered-server-sql-server-management-studio.md)</span><span class="sxs-lookup"><span data-stu-id="73114-131">[Import Registered Server Information &#40;SQL Server Management Studio&#41;](import-registered-server-information-sql-server-management-studio.md) [Create a New Registered Server &#40;SQL Server Management Studio&#41;](create-a-new-registered-server-sql-server-management-studio.md)</span></span>  
  
  
