---
title: 사용자에게 DQS 역할 부여 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: afb445b5-bdbe-4bfe-844f-344766cdc2b2
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 62ff5eb03fa46279ee1b8a1329c58bd69361ef82
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87736790"
---
# <a name="grant-dqs-roles-to-users"></a><span data-ttu-id="9a674-102">사용자에게 DQS 역할 부여</span><span class="sxs-lookup"><span data-stu-id="9a674-102">Grant DQS Roles to Users</span></span>
  <span data-ttu-id="9a674-103">이 항목에서는 Windows 보안 주체를 기반으로 SQL 로그인을 만들고 사용자에게 DQS_MAIN 데이터베이스에 대한 [!INCLUDE[ssDQSnoversion](../../includes/ssdqsnoversion-md.md)] (DQS) 역할을 부여하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="9a674-103">This topic describes how to create SQL logins based on a Windows principal, and grant [!INCLUDE[ssDQSnoversion](../../includes/ssdqsnoversion-md.md)] (DQS) roles on the DQS_MAIN database.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="9a674-104">필수 조건</span><span class="sxs-lookup"><span data-stu-id="9a674-104">Prerequisites</span></span>  
  
-   <span data-ttu-id="9a674-105">DQSInstaller.exe 파일을 실행하여 [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] 설치를 완료해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9a674-105">You must have completed the [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] installation by running the DQSInstaller.exe file.</span></span> <span data-ttu-id="9a674-106">자세한 내용은 [DQSInstaller.exe를 실행하여 Data Quality 서버 설치 완료](run-dqsinstaller-exe-to-complete-data-quality-server-installation.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="9a674-106">For more information, see [Run DQSInstaller.exe to Complete Data Quality Server Installation](run-dqsinstaller-exe-to-complete-data-quality-server-installation.md).</span></span>  
  
-   <span data-ttu-id="9a674-107">SQL 로그인을 만들고 DQS 역할을 부여하려면 Windows 사용자 계정은 적절한 고정 서버 역할(예: securityadmin, serveradmin 또는 sysadmin)의 멤버여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9a674-107">Your Windows user account must be a member of the appropriate fixed server role (such as securityadmin, serveradmin, or sysadmin) to create SQL login, and grant them DQS roles.</span></span>  
  
### <a name="to-create-sql-login-and-grant-dqs-roles"></a><span data-ttu-id="9a674-108">SQL 로그인을 만들고 DQS 역할을 부여하려면</span><span class="sxs-lookup"><span data-stu-id="9a674-108">To create SQL login and grant DQS roles</span></span>  
  
1.  <span data-ttu-id="9a674-109">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="9a674-109">Start [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
2.  <span data-ttu-id="9a674-110">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]에서 SQL Server 인스턴스를 확장한 다음 **보안**을 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="9a674-110">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], expand your SQL Server instance, and then expand **Security**.</span></span>  
  
3.  <span data-ttu-id="9a674-111">**보안** 폴더를 마우스 오른쪽 단추로 클릭하고 **새로 만들기**를 가리킨 다음 **로그인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="9a674-111">Right-click the **Security** folder, point to **New**, and then click **Login**.</span></span>  
  
4.  <span data-ttu-id="9a674-112">**로그인-새로 만들기** 대화 상자에서 **로그인 이름** 상자에 windows 사용자 이름을 지정 하 고 인증 유형으로 **Windows 인증**을 지정한 다음 **검색** 을 클릭 하 여 사용자의 유효성을 검사 합니다.</span><span class="sxs-lookup"><span data-stu-id="9a674-112">In the **Login - New** dialog box, specify the name of a Windows user in the **Login name** box, specify the type of authentication as **Windows authentication**, and click **Search** to validate the user.</span></span>  
  
5.  <span data-ttu-id="9a674-113">사용자 유효성을 확인한 후에 왼쪽 창에서 **사용자 매핑** 페이지를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="9a674-113">After the user is validated, click the **User Mapping** page in the left pane.</span></span>  
  
6.  <span data-ttu-id="9a674-114">오른쪽 창에서 **DQS_MAIN** 데이터베이스에 대해 **매핑** 열 아래의 확인란을 선택한 후 사용자에게 필요한 액세스 수준에 따라 **데이터베이스 역할 멤버 자격: DQS_MAIN**창에서 **dqs_administrator**, **dqs_kb_editor** 또는 **dqs_kb_operator** 확인란을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="9a674-114">In the right pane, select the check box under the **Map** column for the **DQS_MAIN** database, and then select the **dqs_administrator**, **dqs_kb_editor**, or **dqs_kb_operator** check box in the **Database role membership for: DQS_MAIN** pane, depending on the access level needed for the user.</span></span> <span data-ttu-id="9a674-115">세 가지 DQS 역할에 대한 자세한 내용은 [DQS 보안](../dqs-security.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="9a674-115">For information about the three DQS roles, see [DQS Security](../dqs-security.md).</span></span>  
  
7.  <span data-ttu-id="9a674-116">**로그인 – 새로 만들기** 대화 상자에서 **확인**을 클릭하여 변경 내용을 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="9a674-116">In the **Login - New** dialog box, click **OK** to apply the changes.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="9a674-117">사용자에게 **dqs_administrator** 역할을 부여할 경우 변경 내용을 적용한 후 사용자 권한을 다시 확인하면 다른 두 개의 DQS 역할 확인란(**dq_kb_editor** 및 **dqs_kb_operator**)도 함께 선택됩니다.</span><span class="sxs-lookup"><span data-stu-id="9a674-117">If you grant the **dqs_administrator** role to a user, apply the changes, and then recheck the user permissions, the other two DQS roles check boxes (**dq_kb_editor** and **dqs_kb_operator**) are also selected.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="9a674-118">다음 단계</span><span class="sxs-lookup"><span data-stu-id="9a674-118">Next Steps</span></span>  
 <span data-ttu-id="9a674-119">바로 전에 SQL 로그인을 만들고 DQS 역할을 부여한 Windows 사용자 계정을 사용하여 [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] 에 로그인을 시도합니다.</span><span class="sxs-lookup"><span data-stu-id="9a674-119">Try logging on to [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] by using the Windows user account for which you just created a SQL login, and granted a DQS role.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9a674-120">참고 항목</span><span class="sxs-lookup"><span data-stu-id="9a674-120">See Also</span></span>  
 <span data-ttu-id="9a674-121">[Data Quality Services 설치](install-data-quality-services.md) </span><span class="sxs-lookup"><span data-stu-id="9a674-121">[Install Data Quality Services](install-data-quality-services.md) </span></span>  
 [<span data-ttu-id="9a674-122">로그인 만들기</span><span class="sxs-lookup"><span data-stu-id="9a674-122">Create a Login</span></span>](../../relational-databases/security/authentication-access/create-a-login.md)  
  
  
