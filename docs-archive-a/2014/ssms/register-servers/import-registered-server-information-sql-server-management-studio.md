---
title: 등록된 서버 정보 가져오기
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql12.swb.importregisteredservers.f1
helpviewer_keywords:
- transferring registered server information
- Registered Servers [SQL Server], importing
- importing registered server information
ms.assetid: cc497a14-1360-4887-b70c-002f042823b6
author: markingmyname
ms.author: maghan
ms.openlocfilehash: f2eddb3b83f73253e977316767f2b930bc8ab9ff
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87737402"
---
# <a name="import-registered-server-information-sql-server-management-studio"></a><span data-ttu-id="01118-102">등록된 서버 정보 가져오기(SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="01118-102">Import Registered Server Information (SQL Server Management Studio)</span></span>
  <span data-ttu-id="01118-103">이 항목에서는 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]에서 저장된 등록된 서버 정보를 가져오는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="01118-103">This topic describes how to import saved registered server information in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="01118-104">등록된 서버 파일을 내보냈다가 다시 가져오면 등록된 서버에 있는 동일한 서버로 여러 컴퓨터를 쉽게 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="01118-104">Exporting and then importing registered server files lets you easily configure several computers with the same servers in Registered Servers.</span></span> <span data-ttu-id="01118-105">이 작업은 여러 곳에 위치한 컴퓨터에서 다수의 서버를 관리할 때나 경험이 적은 사용자를 위해 기본 연결 설정을 구성하려는 경우에 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="01118-105">This is useful when managing a large number of servers from computers in several locations, or when you want to configure basic connection settings for a less-experienced user.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="01118-106">이전 버전의 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 에 등록된 서버 정보를 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]로 가져올 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="01118-106">You cannot import registered server information into [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] from earlier versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
##  <a name="SSMSProcedure"></a>  
  
#### <a name="to-import-registered-server-information"></a><span data-ttu-id="01118-107">등록된 서버 정보를 가져오려면</span><span class="sxs-lookup"><span data-stu-id="01118-107">To import registered server information</span></span>  
  
1.  <span data-ttu-id="01118-108">등록된 서버의 등록된 서버 도구 모음에서 해당 서버 유형을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="01118-108">In Registered Servers, click the server type on the Registered Servers toolbar.</span></span> <span data-ttu-id="01118-109">서버 유형은 내보낸 파일의 등록된 서버 유형과 같아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="01118-109">The server type must be the same as the registered server export file type.</span></span> <span data-ttu-id="01118-110">예를 들어 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 로 등록된 서버 정보를 내보낸 경우 등록된 서버 도구 모음에서 **SQL Server** 를 클릭해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="01118-110">For example, if you have exported [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] registered server information, you must click **SQL Server** on the Registered Servers toolbar.</span></span>  
  
2.  <span data-ttu-id="01118-111">서버 그룹을 마우스 오른쪽 단추로 클릭한 다음 **가져오기**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="01118-111">Right-click a server group, and select **Import**.</span></span>  
  
3.  <span data-ttu-id="01118-112">**등록된 서버 가져오기** 대화 상자에서 가져오려는 등록된 서버 파일을 선택한 다음 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="01118-112">In the **Import Registered Servers** dialog box, select the registered servers file to import, and then click **OK**.</span></span>  
  
     <span data-ttu-id="01118-113">**파일 가져오기**</span><span class="sxs-lookup"><span data-stu-id="01118-113">**Import file**</span></span>  
     <span data-ttu-id="01118-114">입력란에 가져올 파일 이름을 입력하거나 찾아보기 단추( **...** )를 클릭하여 클라이언트 컴퓨터에서 가져올 파일을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="01118-114">Type the name of the import file in the text box, or click the Browse button (**...**) to locate the import file on the client computer.</span></span> <span data-ttu-id="01118-115">기존 파일을 선택하면 등록된 서버 정보가 파일에 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="01118-115">If you select an existing file, the registered server information is appended to the file.</span></span> <span data-ttu-id="01118-116">이전에 내보낸 등록된 서버 파일만 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="01118-116">The import file can only be a previously exported registered server file.</span></span> <span data-ttu-id="01118-117">등록된 서버 파일의 확장자는 .regsrvr입니다.</span><span class="sxs-lookup"><span data-stu-id="01118-117">Registered server files have a .regsrvr extension.</span></span>  
  
     <span data-ttu-id="01118-118">**가져올 서버 그룹을 선택하세요.**</span><span class="sxs-lookup"><span data-stu-id="01118-118">**Select the server group to import to**</span></span>  
     <span data-ttu-id="01118-119">파일의 등록된 서버 항목을 가져올 루트 노드나 특정 서버 그룹을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="01118-119">Select the root node or a particular server group to which the registered server entries in the file will be imported.</span></span> <span data-ttu-id="01118-120">등록된 모든 서버, 특정 서버 그룹에 속한 등록된 서버 또는 등록된 단일 서버를 내보내기 파일로 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="01118-120">You can import all registered servers, registered servers in a particular server group, or a single registered server to the export file.</span></span> <span data-ttu-id="01118-121">가져오기 기능은 재귀적입니다. 예를 들어 서버 그룹 A에는 서버 그룹 B가, 서버 그룹 B에는 서버 그룹 C와 D가 포함된 경우 서버 그룹 A를 가져오면 A, B, C, D의 모든 항목이 내보내집니다.</span><span class="sxs-lookup"><span data-stu-id="01118-121">The import functionality is recursive; for example, if server group A contains server group B, and server group B contains server groups C and D, importing server group A exports all entries in A, B, C, and D.</span></span>  
  
     <span data-ttu-id="01118-122">서버 그룹은 현재 등록된 서버 트리의 서버 그룹만 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="01118-122">The server group displays only the server groups of the current registered server tree.</span></span>  
  
     <span data-ttu-id="01118-123">기존 서버 그룹이나 서버를 가져오도록 선택하면 기존 서버나 서버 그룹을 덮어쓸지 확인하는 메시지가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="01118-123">If you select to import an existing server group or server, a message confirms that you want to overwrite the existing server or server group.</span></span>  
  
 <span data-ttu-id="01118-124">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인증을 사용하는 서버 등록은 사용자 단위로 암호를 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="01118-124">Server registrations that use [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication store passwords on a per-user basis.</span></span> <span data-ttu-id="01118-125">서버 등록을 가져온 후 사용자는 처음으로 연결할 때 각 서버의 암호를 입력하여 등록된 서버 목록에 암호를 저장해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="01118-125">After importing the server registrations, users must enter the password for each server the first time they connect, storing the passwords in their lists of registered servers.</span></span> <span data-ttu-id="01118-126">Windows 인증을 통해 등록된 서버에는 이 작업이 필요 없습니다.</span><span class="sxs-lookup"><span data-stu-id="01118-126">This is not necessary for servers registered through Windows Authentication.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="01118-127">참고 항목</span><span class="sxs-lookup"><span data-stu-id="01118-127">See Also</span></span>  
 <span data-ttu-id="01118-128">[서버 등록 &#40;SQL Server Management Studio 변경 하&#41;](change-a-server-s-registration-sql-server-management-studio.md) [등록 된 서버 정보 내보내기 &#40;SQL Server Management Studio&#41;](export-registered-server-information-sql-server-management-studio.md) </span><span class="sxs-lookup"><span data-stu-id="01118-128">[Change a Server's Registration &#40;SQL Server Management Studio&#41;](change-a-server-s-registration-sql-server-management-studio.md) [Export Registered Server Information &#40;SQL Server Management Studio&#41;](export-registered-server-information-sql-server-management-studio.md) </span></span>  
 [<span data-ttu-id="01118-129">새 등록된 서버 만들기&#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="01118-129">Create a New Registered Server &#40;SQL Server Management Studio&#41;</span></span>](create-a-new-registered-server-sql-server-management-studio.md)  
  
  
