---
title: 정책 기반 관리 정책 가져오기 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Policy-Based Management, import policy
ms.assetid: 850b7ef9-d2b7-4754-bf04-7cb419ffb776
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: d83ed589e147c61b1692447aacb17535f18a5c9e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646977"
---
# <a name="import-a-policy-based-management-policy"></a><span data-ttu-id="3eef3-102">정책 기반 관리 정책 가져오기</span><span class="sxs-lookup"><span data-stu-id="3eef3-102">Import a Policy-Based Management Policy</span></span>
  <span data-ttu-id="3eef3-103">이 항목에서는 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 를 사용하여 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]에서 정책 기반 관리 정책 인스턴스를 가져오는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="3eef3-103">This topic describes how to import a Policy-Based Management policy instance in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="3eef3-104">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="3eef3-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="3eef3-105">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="3eef3-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="3eef3-106">제한 사항</span><span class="sxs-lookup"><span data-stu-id="3eef3-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="3eef3-107">보안</span><span class="sxs-lookup"><span data-stu-id="3eef3-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="3eef3-108">**다음을 사용하여 정책 인스턴스를 가져오려면**</span><span class="sxs-lookup"><span data-stu-id="3eef3-108">**To import a policy instance, using:**</span></span>  
  
     [<span data-ttu-id="3eef3-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="3eef3-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="3eef3-110">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="3eef3-110">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="3eef3-111">제한 사항</span><span class="sxs-lookup"><span data-stu-id="3eef3-111">Limitations and Restrictions</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="3eef3-112">는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]인스턴스를 모니터링하는 데 사용할 수 있는 정책과 함께 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="3eef3-112">ships with policies that can be used to monitor an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="3eef3-113">기본적으로 이러한 정책은 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]에 설치되지 않지만 기본 위치인 C:\Program Files\Microsoft SQL Server\120\Tools\Policies\DatabaseEngine\1042에서 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3eef3-113">By default, these policies are not installed on the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], but they can be imported from the default location of C:\Program Files\Microsoft SQL Server\120\Tools\Policies\DatabaseEngine\1033.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="3eef3-114">보안</span><span class="sxs-lookup"><span data-stu-id="3eef3-114">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="3eef3-115">권한</span><span class="sxs-lookup"><span data-stu-id="3eef3-115">Permissions</span></span>  
 <span data-ttu-id="3eef3-116">msdb 데이터베이스에서 PolicyAdministratorRole 역할의 멤버 자격이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="3eef3-116">Requires membership in the PolicyAdministratorRole role in the msdb database.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="3eef3-117">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="3eef3-117">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-import-a-policy-instance"></a><span data-ttu-id="3eef3-118">정책 인스턴스를 가져오려면</span><span class="sxs-lookup"><span data-stu-id="3eef3-118">To import a policy instance</span></span>  
  
1.  <span data-ttu-id="3eef3-119">**개체 탐색기**에서 더하기 기호를 클릭하여 새로 가져온 정책 인스턴스가 상주할 서버를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="3eef3-119">In **Object Explorer**, click the plus sign to expand the server where the newly-imported policy instance will reside.</span></span>  
  
2.  <span data-ttu-id="3eef3-120">더하기 기호를 클릭하여 **관리** 폴더를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="3eef3-120">Click the plus sign to expand the **Management** folder.</span></span>  
  
3.  <span data-ttu-id="3eef3-121">더하기 기호를 클릭하여 **정책 관리**를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="3eef3-121">Click the plus sign to expand **Policy Management**.</span></span>  
  
4.  <span data-ttu-id="3eef3-122">**정책** 폴더를 마우스 오른쪽 단추로 클릭하고 **정책 가져오기**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="3eef3-122">Right-click the **Policies** folder and select **Import Policy**.</span></span>  
  
5.  <span data-ttu-id="3eef3-123">**가져오기** 대화 상자에서 파일의 경로와 이름을 입력하거나 찾아보기( **...** ) 단추를 사용하여 정책이 포함된 XML 파일을 찾은 다음 파일을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="3eef3-123">In the **Import** dialog box, type the path and name of the file; or use the Browse (**...**) button to locate the XML file that contains the policy, and then select the file.</span></span> <span data-ttu-id="3eef3-124">**가져오기** 대화 상자에서 사용할 수 있는 옵션에 대한 자세한 내용은 [Import Policies Dialog Box](import-policies-dialog-box.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3eef3-124">For more information on the available options in the **Import** dialog box, see [Import Policies Dialog Box](import-policies-dialog-box.md).</span></span>  
  
6.  <span data-ttu-id="3eef3-125">완료되었으면 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3eef3-125">When finished, click **OK**.</span></span>  
  
  
