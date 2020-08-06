---
title: 원본 제어 연결 변경 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- connections [SQL Server Management Studio], source controls
- source controls [SQL Server Management Studio], connections
ms.assetid: 538e3beb-f99c-4095-bd65-6413e872d26e
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 077a09cdca0c0aff777184f04467ca39592690aa
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652365"
---
# <a name="change-source-control-connections"></a><span data-ttu-id="e7173-102">원본 제어 연결 변경</span><span class="sxs-lookup"><span data-stu-id="e7173-102">Change Source Control Connections</span></span>
  <span data-ttu-id="e7173-103">소스 제어에서 솔루션을 처음 추가하거나 열면 원본 제어 공급자는 로컬 솔루션 디렉터리의 루트 폴더와 해당 서버 폴더 간에 연결을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="e7173-103">The first time you add or open a solution from source control, your source control provider creates an association between the root folder of the local solution directory and its corresponding server folder.</span></span>  
  
 <span data-ttu-id="e7173-104">루트 폴더(통합 루트라고도 함)는 클라이언트에 상주합니다.</span><span class="sxs-lookup"><span data-stu-id="e7173-104">The root folder (also called unified root) resides on the client.</span></span> <span data-ttu-id="e7173-105">루트 폴더는 솔루션이나 프로젝트가 참조하는 모든 파일을 그 아래에서 찾을 수 있는 폴더입니다.</span><span class="sxs-lookup"><span data-stu-id="e7173-105">It is the folder beneath which all the files referenced by a solution or project can be found.</span></span> <span data-ttu-id="e7173-106">최신 버전의 솔루션, 기록 및 상태 정보를 찾으려면 소스 제어 서버에 상주하는 서버 폴더를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="e7173-106">To find the latest version of a solution, its history, and its status information, locate the server folder, which resides on the source control server.</span></span> <span data-ttu-id="e7173-107">[!INCLUDE[msCoName](../includes/msconame-md.md)] Visual SourceSafe에서는 서버 폴더를 프로젝트라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="e7173-107">In [!INCLUDE[msCoName](../includes/msconame-md.md)] Visual SourceSafe, server folders are called projects.</span></span>  
  
 <span data-ttu-id="e7173-108">대부분의 상황에서는 해당 서버 폴더에서 솔루션을 언바인딩하거나 솔루션 연결을 끊어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e7173-108">In many situations, you need to unbind or disconnect a solution from its server folder.</span></span> <span data-ttu-id="e7173-109">예를 들어 소스 제어 공급자가 상주하는 컴퓨터를 사용할 수 없는 경우 백업 컴퓨터에 연결하여 솔루션을 백업된 서버 폴더에 다시 바인딩하고 작업을 정상적으로 재개할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e7173-109">For example, if the computer on which your source control provider resides is unavailable, you can connect to a backup computer, rebind your solution to a backed-up server folder, and resume working normally.</span></span> <span data-ttu-id="e7173-110">또한 소스 제어 프로젝트가 분기된 경우 새 프로젝트 버전이 상주하는 서버 폴더에 솔루션을 바인딩해야 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e7173-110">Also, if a source control project is forked, you may have to bind your solution to the server folder where the new project version resides.</span></span>  
  
 <span data-ttu-id="e7173-111">소스 제어 공급자의 사용자 인터페이스를 사용하여 솔루션이 바인딩되는 서버 폴더를 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e7173-111">Use the user interface of the source control provider to change the server folder that a solution is bound to.</span></span> <span data-ttu-id="e7173-112">[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 환경 내에서 소스 제어 사용자 인터페이스를 열 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e7173-112">You can open the source control user interface from within the [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] environment.</span></span>  
  
#### <a name="to-open-the-source-control-user-interface-from-the-studio-environment"></a><span data-ttu-id="e7173-113">Studio 환경에서 소스 제어 사용자 인터페이스를 열려면</span><span class="sxs-lookup"><span data-stu-id="e7173-113">To open the source control user interface from the Studio environment</span></span>  
  
1.  <span data-ttu-id="e7173-114">**파일** 메뉴에서 **원본 제어**를 가리킨 다음 **Microsoft Visual SourceSafe 시작**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="e7173-114">On the **File** menu, point to **Source Control**, and then click **Launch Microsoft Visual SourceSafe**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e7173-115">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e7173-115">See Also</span></span>  
 <span data-ttu-id="e7173-116">[원본 제어 기본 사항](../../2014/database-engine/source-control-basics.md) </span><span class="sxs-lookup"><span data-stu-id="e7173-116">[Source Control Basics](../../2014/database-engine/source-control-basics.md) </span></span>  
 <span data-ttu-id="e7173-117">[원본 제어 옵션 설정](../../2014/database-engine/set-source-control-options.md) </span><span class="sxs-lookup"><span data-stu-id="e7173-117">[Set Source Control Options](../../2014/database-engine/set-source-control-options.md) </span></span>  
 [<span data-ttu-id="e7173-118">소스 제어에서 파일 제외</span><span class="sxs-lookup"><span data-stu-id="e7173-118">Exclude Files from Source Control</span></span>](../../2014/database-engine/exclude-files-from-source-control.md)  
  
  
