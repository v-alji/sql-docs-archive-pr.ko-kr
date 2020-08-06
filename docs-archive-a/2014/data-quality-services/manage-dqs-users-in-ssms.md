---
title: SSMS에서 DQS 사용자 관리 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 955af01d-00da-4c51-9311-f3848749df54
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: bf8789abb59d168f39562f6486bb5c54bfc0fc50
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660141"
---
# <a name="manage-dqs-users-in-ssms"></a><span data-ttu-id="f25fc-102">SSMS에서 DQS 사용자 관리</span><span class="sxs-lookup"><span data-stu-id="f25fc-102">Manage DQS Users in SSMS</span></span>
  <span data-ttu-id="f25fc-103">이 항목에서는 SQL Server Management Studio를 사용하여 SQL Server 인스턴스에서 추가 사용자를 만들고 사용자에게 DQS_MAIN 데이터베이스에 대한 적절한 DQS( [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] ) 역할을 부여하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="f25fc-103">This topic describes how to create additional users in the SQL Server instance using SQL Server Management Studio, and grant them appropriate [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS) roles on the DQS_MAIN database.</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="f25fc-104">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="f25fc-104">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="f25fc-105">보안</span><span class="sxs-lookup"><span data-stu-id="f25fc-105">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="f25fc-106">권한</span><span class="sxs-lookup"><span data-stu-id="f25fc-106">Permissions</span></span>  
 <span data-ttu-id="f25fc-107">SQL 로그인을 만들고 적절한 DQS 역할을 부여하려면 Windows 사용자 계정은 적절한 고정 서버 역할(예: securityadmin, serveradmin 또는 sysadmin)의 멤버여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f25fc-107">Your Windows user account must be a member of the appropriate fixed server role (such as securityadmin, serveradmin, or sysadmin) to create SQL login, and grant appropriate DQS roles.</span></span>  
  
##  <a name="create-a-sql-login-and-grant-dqs-role"></a><a name="GrantRoles"></a><span data-ttu-id="f25fc-108">SQL 로그인을 만들고 DQS 역할을 부여 합니다.</span><span class="sxs-lookup"><span data-stu-id="f25fc-108">Create a SQL Login and Grant DQS Role</span></span>  
  
1.  <span data-ttu-id="f25fc-109">Microsoft SQL Server Management Studio를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="f25fc-109">Start Microsoft SQL Server Management Studio.</span></span>  
  
2.  <span data-ttu-id="f25fc-110">Microsoft SQL Server Management Studio에서 해당 SQL Server 인스턴스를 확장하고 **보안**을 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="f25fc-110">In Microsoft SQL Server Management Studio, expand your SQL Server instance, and then expand **Security**.</span></span>  
  
3.  <span data-ttu-id="f25fc-111">**보안** 폴더를 마우스 오른쪽 단추로 클릭하고 **새로 만들기**를 가리킨 다음 **로그인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f25fc-111">Right-click the **Security** folder, point to **New**, and then click **Login**.</span></span>  
  
4.  <span data-ttu-id="f25fc-112">**로그인-새로 만들기** 대화 상자에서 **로그인 이름** 상자에 windows 사용자 이름을 지정 하 고 인증 유형으로 **Windows 인증**을 지정한 다음 **검색** 을 클릭 하 여 사용자의 유효성을 검사 합니다.</span><span class="sxs-lookup"><span data-stu-id="f25fc-112">In the **Login - New** dialog box, specify the name of a Windows user in the **Login name** box, specify the type of authentication as **Windows authentication**, and click **Search** to validate the user.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="f25fc-113">DQS는 Windows 인증만 지원하며 SQL Server 인증은 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f25fc-113">DQS only supports Windows authentication; SQL Server authentication is not supported.</span></span>  
  
5.  <span data-ttu-id="f25fc-114">사용자 유효성을 확인한 후에 왼쪽 창에서 **사용자 매핑** 페이지를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f25fc-114">After the user is validated, click the **User Mapping** page in the left pane.</span></span>  
  
6.  <span data-ttu-id="f25fc-115">오른쪽 창에서 **DQS_MAIN** 데이터베이스에 대해 **매핑** 열 아래의 확인란을 선택한 후 사용자에게 필요한 액세스 수준에 따라 **데이터베이스 역할 멤버 자격: DQS_MAIN**창에서 **dqs_administrator**, **dqs_kb_editor** 또는 **dqs_kb_operator** 확인란을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="f25fc-115">In the right pane, select the check box under the **Map** column for the **DQS_MAIN** database, and then select the **dqs_administrator**, **dqs_kb_editor**, or **dqs_kb_operator** check box in the **Database role membership for: DQS_MAIN** pane, depending on the access level needed for the user.</span></span>  
  
7.  <span data-ttu-id="f25fc-116">**로그인 – 새로 만들기** 대화 상자에서 **확인**을 클릭하여 변경 내용을 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="f25fc-116">In the **Login - New** dialog box, click **OK** to apply the changes.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="f25fc-117">사용자에게 **dqs_administrator** 역할을 부여할 경우 변경 내용을 적용한 후 사용자 권한을 다시 확인하면 다른 두 개의 DQS 역할 확인란(**dq_kb_editor** 및 **dqs_kb_operator**)도 함께 선택됩니다.</span><span class="sxs-lookup"><span data-stu-id="f25fc-117">If you grant the **dqs_administrator** role to a user, apply the changes, and then recheck the user permissions, the other two DQS roles check boxes (**dq_kb_editor** and **dqs_kb_operator**) are also selected.</span></span>  
  
  
