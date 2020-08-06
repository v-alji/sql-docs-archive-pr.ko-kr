---
title: 정책 기반 관리 정책 내보내기 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Policy-Based Management, export policy
ms.assetid: f0001b33-9078-4432-8460-496736fb325a
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 15f554aeeebfd47c3fa1ea13b100fbe6bcfcc055
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651664"
---
# <a name="export-a-policy-based-management-policy"></a><span data-ttu-id="b1bda-102">정책 기반 관리 정책 내보내기</span><span class="sxs-lookup"><span data-stu-id="b1bda-102">Export a Policy-Based Management Policy</span></span>
  <span data-ttu-id="b1bda-103">이 항목에서는 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 를 사용하여 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]에서 정책 기반 관리 정책을 내보내는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="b1bda-103">This topic describes how to export a Policy-Based Management policy in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="b1bda-104">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="b1bda-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="b1bda-105">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="b1bda-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="b1bda-106">보안</span><span class="sxs-lookup"><span data-stu-id="b1bda-106">Security</span></span>](#Security)  
  
-   <span data-ttu-id="b1bda-107">**다음을 사용하여 정책을 내보내려면:**</span><span class="sxs-lookup"><span data-stu-id="b1bda-107">**To export a policy, using:**</span></span>  
  
     [<span data-ttu-id="b1bda-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="b1bda-108">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="b1bda-109">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="b1bda-109">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="b1bda-110">보안</span><span class="sxs-lookup"><span data-stu-id="b1bda-110">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="b1bda-111">권한</span><span class="sxs-lookup"><span data-stu-id="b1bda-111">Permissions</span></span>  
 <span data-ttu-id="b1bda-112">msdb 데이터베이스에서 PolicyAdministratorRole 역할의 멤버 자격이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="b1bda-112">Requires membership in the PolicyAdministratorRole role in the msdb database.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="b1bda-113">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="b1bda-113">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-export-a-policy"></a><span data-ttu-id="b1bda-114">정책을 내보내려면</span><span class="sxs-lookup"><span data-stu-id="b1bda-114">To export a policy</span></span>  
  
1.  <span data-ttu-id="b1bda-115">개체 탐색기에서 더하기 기호를 클릭하여 내보내려는 정책 기반 관리 정책이 들어 있는 서버를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="b1bda-115">In Object Explorer, click the plus sign to expand the server that contains the Policy-Based Management policy that you want to export.</span></span>  
  
2.  <span data-ttu-id="b1bda-116">더하기 기호를 클릭하여 **관리** 폴더를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="b1bda-116">Click the plus sign to expand the **Management** folder.</span></span>  
  
3.  <span data-ttu-id="b1bda-117">더하기 기호를 클릭하여 **정책 관리**를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="b1bda-117">Click the plus sign to expand **Policy Management**.</span></span>  
  
4.  <span data-ttu-id="b1bda-118">더하기 기호를 클릭하여 **정책** 폴더를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="b1bda-118">Click the plus sign to expand the **Policies** folder.</span></span>  
  
5.  <span data-ttu-id="b1bda-119">내보내려는 정책을 마우스 오른쪽 단추로 클릭하고 **정책 내보내기**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="b1bda-119">Right-click the policy that you want to export and select **Export Policy**.</span></span>  
  
6.  <span data-ttu-id="b1bda-120">**정책 내보내기** 대화 상자의 주소 표시줄에 파일의 경로와 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="b1bda-120">In the **Export Policy** dialog box, type the path and name of the file in the address bar.</span></span> <span data-ttu-id="b1bda-121">또는 이 대화 상자의 탐색 창에서 파일에 적합한 위치를 찾은 다음 **파일 이름** 상자에 XML 파일의 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="b1bda-121">Alternately, find a suitable location for the file in the dialog box's navigation pane, and then type the name of the XML file in the **File Name** box.</span></span>  
  
7.  <span data-ttu-id="b1bda-122">완료되면 **저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b1bda-122">When finished, click **Save**.</span></span>  
  
  
