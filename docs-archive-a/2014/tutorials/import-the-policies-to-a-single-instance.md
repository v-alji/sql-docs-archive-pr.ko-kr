---
title: 단일 인스턴스로 정책 가져오기 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
ms.assetid: bc5bcd87-663f-41d9-bb7b-b3e083cd63df
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 0464bc6f4dcd6326a4b8f222cb4b3128f21561ca
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740606"
---
# <a name="import-the-policies-to-a-single-instance"></a><span data-ttu-id="38ba1-102">단일 인스턴스로 정책 가져오기</span><span class="sxs-lookup"><span data-stu-id="38ba1-102">Import the Policies to a Single Instance</span></span>
  <span data-ttu-id="38ba1-103">이 태스크에서는 단일 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]인스턴스에서 예약할 최선의 구현 방법 정책을 정책 기반 관리로 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="38ba1-103">In this task, you will import the best practices policies that you want to schedule into Policy-Based Management on a single instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="38ba1-104">사전 요구 사항</span><span class="sxs-lookup"><span data-stu-id="38ba1-104">Prerequisites</span></span>  
 <span data-ttu-id="38ba1-105">[!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] 이상 버전이 실행되는 서버에서 이 절차를 수행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="38ba1-105">You must perform this procedure on a server that is running [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] or a later version.</span></span>  
  
### <a name="import-the-best-practices-policies-for-the-database-engine"></a><span data-ttu-id="38ba1-106">데이터베이스 엔진에 대한 최선의 구현 방법 정책 가져오기</span><span class="sxs-lookup"><span data-stu-id="38ba1-106">Import the best practices policies for the Database Engine</span></span>  
  
1.  <span data-ttu-id="38ba1-107">[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]를 시작하고 [!INCLUDE[ssDE](../includes/ssde-md.md)]에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="38ba1-107">Start [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], and then connect to the [!INCLUDE[ssDE](../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="38ba1-108">개체 탐색기에서 **관리**를 확장한 다음 **정책 관리**를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="38ba1-108">In Object Explorer, expand **Management**, and then expand **Policy Management**.</span></span>  
  
3.  <span data-ttu-id="38ba1-109">**정책**을 마우스 오른쪽 단추로 클릭한 다음 **정책 가져오기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="38ba1-109">Right-click **Policies**, and then click **Import Policy**.</span></span>  
  
4.  <span data-ttu-id="38ba1-110">**가져오기** 대화 상자에서 **가져올 파일** 상자 옆에 있는 줄임표 (**...**) 단추를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="38ba1-110">In the **Import** dialog box, next to the **Files to import** box, click the ellipsis (**...**) button.</span></span>  
  
5.  <span data-ttu-id="38ba1-111">**찾는 위치** 목록에서 최선의 구현 방법 정책이 포함된 다음 폴더를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="38ba1-111">In the **Look in** list, browse to the following folder, which contains the best practices policies:</span></span>  
  
     <span data-ttu-id="38ba1-112">**C:\Program Files (x86)\Microsoft SQL Server\110\Tools\Policies\DatabaseEngine\1033**</span><span class="sxs-lookup"><span data-stu-id="38ba1-112">**C:\Program Files (x86)\Microsoft SQL Server\110\Tools\Policies\DatabaseEngine\1033**</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="38ba1-113">파일 경로는 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 프로그램 파일의 설치 위치, 32비트 운영 체제를 실행하는지 아니면 64비트 운영 체제를 실행하는지 여부 및 언어 식별자에 따라 달라질 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="38ba1-113">The file path may vary, depending on where you installed the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] program files, whether you are running a 32-bit or 64-bit operating system, and the language identifier.</span></span>  
  
6.  <span data-ttu-id="38ba1-114">**정책 선택** 대화 상자에서 하나 이상의 정책 파일을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="38ba1-114">In the **Select Policy** dialog box, select one or more policy files.</span></span>  
  
     <span data-ttu-id="38ba1-115">인접하지 않은 파일을 선택하려면 파일 한 개를 클릭하고 Ctrl 키를 누른 채 추가 파일을 각각 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="38ba1-115">To select nonadjacent files, click one file, hold down the CTRL key, and then click each additional file.</span></span> <span data-ttu-id="38ba1-116">인접 파일을 선택하려면 시퀀스의 첫 번째 파일을 클릭하고 Shift 키를 누른 채 마지막 파일을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="38ba1-116">To select adjacent files, click the first file in the sequence, hold down the SHIFT key, and then click the last file.</span></span>  
  
7.  <span data-ttu-id="38ba1-117">파일 선택을 마쳤으면 **열기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="38ba1-117">When you are finished selecting files, click **Open**.</span></span>  
  
8.  <span data-ttu-id="38ba1-118">**가져오기** 대화 상자에서 **정책 상태** 목록이 **가져올 때 정책 상태 유지** (기본값)로 설정되어 있는지 확인한 다음 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="38ba1-118">In the **Import** dialog box, make sure that the **Policy state** list is set to **Preserve policy state on import** (the default), and then click **OK**.</span></span>  
  
     <span data-ttu-id="38ba1-119">정책을 **정책 관리** 아래의 **정책**노드로 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="38ba1-119">The policies are imported into the **Policies** node under **Policy Management**.</span></span> <span data-ttu-id="38ba1-120">가져온 정책은 기본적으로 "요청 시" 평가 모드로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="38ba1-120">By default, the imported policies are set to "On demand" evaluation mode.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="38ba1-121">다음 단계</span><span class="sxs-lookup"><span data-stu-id="38ba1-121">Next Steps</span></span>  
 [<span data-ttu-id="38ba1-122">정책 예약</span><span class="sxs-lookup"><span data-stu-id="38ba1-122">Schedule the Policies</span></span>](../../2014/tutorials/schedule-the-policies.md)  
  
  
