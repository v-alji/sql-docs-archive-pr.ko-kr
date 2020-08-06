---
title: RSExecRole 만들기 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- RSExecRole
ms.assetid: 7ac17341-df7e-4401-870e-652caa2859c0
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 0037ef0c4d7a949b5a30bb45356613f6114db130
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87731400"
---
# <a name="create-the-rsexecrole"></a><span data-ttu-id="d2c31-102">RSExecRole 만들기</span><span class="sxs-lookup"><span data-stu-id="d2c31-102">Create the RSExecRole</span></span>
  [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]<span data-ttu-id="d2c31-103">는 `RSExecRole`이라는 미리 정의된 데이터베이스 역할을 사용하여 보고서 서버 데이터베이스에 대한 보고서 서버 사용 권한을 부여합니다.</span><span class="sxs-lookup"><span data-stu-id="d2c31-103">uses a predefined database role called `RSExecRole` to grant report server permissions to the report server database.</span></span> <span data-ttu-id="d2c31-104">`RSExecRole` 역할은 보고서 서버 데이터베이스와 함께 자동으로 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="d2c31-104">The `RSExecRole` role is created automatically with the report server database.</span></span> <span data-ttu-id="d2c31-105">일반적으로 이 역할을 수정하거나 다른 사용자를 이 역할에 할당해서는 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d2c31-105">As a rule, you should never modify it or assign other users to the role.</span></span> <span data-ttu-id="d2c31-106">그러나 보고서 서버 데이터베이스를 새 또는 다른로 이동 하는 경우 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../../includes/ssde-md.md)] 에는 MASTER 및 MSDB 시스템 데이터베이스에서 해당 역할을 다시 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d2c31-106">However, when you move a report server database to a new or different [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../../includes/ssde-md.md)], must re-create the role in the Master and MSDB system databases.</span></span>

 <span data-ttu-id="d2c31-107">아래 지침에 따라 다음 단계를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="d2c31-107">Using the following instructions, you will perform the following steps:</span></span>

-   <span data-ttu-id="d2c31-108">Master 시스템 데이터베이스에서 `RSExecRole`을 만들고 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="d2c31-108">Create and provision the `RSExecRole` in the Master system database.</span></span>

-   <span data-ttu-id="d2c31-109">MSDB 시스템 데이터베이스에서 `RSExecRole`을 만들고 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="d2c31-109">Create and provision the `RSExecRole` in the MSDB system database.</span></span>

> [!NOTE]
>  <span data-ttu-id="d2c31-110">이 항목의 지침은 보고서 서버 데이터베이스를 제공하기 위해 WMI 코드를 작성하거나 스크립트를 실행하지 않으려는 사용자를 위한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="d2c31-110">The instructions in this topic are intended for users who do not want to run a script or write WMI code to provision the report server database.</span></span> <span data-ttu-id="d2c31-111">큰 배포를 관리하며 데이터베이스를 정기적으로 이동하는 경우에는 스크립트를 작성하여 이러한 단계를 자동화해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d2c31-111">If you manage a large deployment and will be moving databases routinely, you should write a script to automate these steps.</span></span> <span data-ttu-id="d2c31-112">자세한 내용은 [Reporting Services WMI 공급자 액세스](../tools/access-the-reporting-services-wmi-provider.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d2c31-112">For more information, see [Access the Reporting Services WMI Provider](../tools/access-the-reporting-services-wmi-provider.md).</span></span>

## <a name="before-you-start"></a><span data-ttu-id="d2c31-113">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="d2c31-113">Before you start</span></span>

-   <span data-ttu-id="d2c31-114">데이터베이스를 이동한 후 암호화 키를 복원할 수 있도록 해당 키를 백업합니다.</span><span class="sxs-lookup"><span data-stu-id="d2c31-114">Back up the encryption keys so that you can restore them after the database is moved.</span></span> <span data-ttu-id="d2c31-115">이 단계는 `RSExecRole`을 만들고 제공하는 기능에 직접적인 영향을 주지는 않지만 작업을 확인하려면 해당 키의 백업이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d2c31-115">This is step does not directly affect your ability to create and provision the `RSExecRole`, but you must have a backup of the keys in order to verify your work.</span></span> <span data-ttu-id="d2c31-116">자세한 내용은 [Back Up and Restore Reporting Services Encryption Keys](../install-windows/ssrs-encryption-keys-back-up-and-restore-encryption-keys.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d2c31-116">For more information, see [Back Up and Restore Reporting Services Encryption Keys](../install-windows/ssrs-encryption-keys-back-up-and-restore-encryption-keys.md).</span></span>

-   <span data-ttu-id="d2c31-117">`sysadmin` 인스턴스에 대한 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 권한이 있는 사용자 계정으로 로그온했는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="d2c31-117">Verify you are logged on as a user account that has `sysadmin` permissions on the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] instance.</span></span>

-   <span data-ttu-id="d2c31-118">사용할 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 인스턴스에 [!INCLUDE[ssDE](../../../includes/ssde-md.md)] 에이전트 서비스가 설치되어 실행되고 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="d2c31-118">Verify [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent service is installed and running on the instance of the [!INCLUDE[ssDE](../../../includes/ssde-md.md)] instance that you plan to use.</span></span>

-   <span data-ttu-id="d2c31-119">reportservertempdb 데이터베이스와 reportserver 데이터베이스를 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="d2c31-119">Attach the reportservertempdb and reportserver databases.</span></span> <span data-ttu-id="d2c31-120">이러한 데이터베이스를 연결하지 않고도 실제 역할을 만들 수 있지만 작업을 테스트하려면 해당 데이터베이스를 연결해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d2c31-120">You are not required to attach the databases to create the actual role, but they must be attached before you can test your work.</span></span>

 <span data-ttu-id="d2c31-121">`RSExecRole`을 수동으로 만드는 작업에 대한 지침은 보고서 서버 설치를 마이그레이션하는 컨텍스트 내에서 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d2c31-121">The instructions for manually creating the `RSExecRole` are intended to be used within the context of migrating a report server installation.</span></span> <span data-ttu-id="d2c31-122">보고서 서버 데이터베이스 백업 및 이동과 같은 중요한 태스크는 이 항목에서 다루지 않지만 데이터베이스 엔진 설명서에 문서화되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d2c31-122">Important tasks such as backing up and moving the report server database are not addressed in this topic, but are documented in the Database Engine documentation.</span></span>

## <a name="create-rsexecrole-in-master"></a><span data-ttu-id="d2c31-123">Master에서 RSExecRole 만들기</span><span class="sxs-lookup"><span data-stu-id="d2c31-123">Create RSExecRole in Master</span></span>
 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] <span data-ttu-id="d2c31-124">는 예약된 작업을 지원하기 위해 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 에이전트 서비스에 대해 확장 저장 프로시저를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="d2c31-124">uses extended stored procedures for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent service to support scheduled operations.</span></span> <span data-ttu-id="d2c31-125">다음 단계에서는 해당 프로시저에 대한 Execute 권한을 `RSExecRole` 역할에 부여하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="d2c31-125">The following steps explain how to grant Execute permissions for the procedures to the `RSExecRole` role.</span></span>

#### <a name="to-create-rsexecrole-in-the-master-system-database-using-management-studio"></a><span data-ttu-id="d2c31-126">Management Studio를 사용하여 Master 시스템 데이터베이스에서 RSExecRole을 만들려면</span><span class="sxs-lookup"><span data-stu-id="d2c31-126">To create RSExecRole in the Master system database using Management Studio</span></span>

1.  <span data-ttu-id="d2c31-127">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]를 시작하고 보고서 서버 인스턴스를 호스팅하는 [!INCLUDE[ssDE](../../../includes/ssde-md.md)] 인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="d2c31-127">Start [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] and connect to the [!INCLUDE[ssDE](../../../includes/ssde-md.md)] instance that hosts the report server database.</span></span>

2.  <span data-ttu-id="d2c31-128">**데이터베이스**를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="d2c31-128">Open **Databases**.</span></span>

3.  <span data-ttu-id="d2c31-129">**시스템 데이터베이스**를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="d2c31-129">Open **System Databases**.</span></span>

4.  <span data-ttu-id="d2c31-130">`Master`를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="d2c31-130">Open `Master`.</span></span>

5.  <span data-ttu-id="d2c31-131">**보안**을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="d2c31-131">Open **Security**.</span></span>

6.  <span data-ttu-id="d2c31-132">**역할**을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="d2c31-132">Open **Roles**.</span></span>

7.  <span data-ttu-id="d2c31-133">**데이터베이스 역할**을 마우스 오른쪽 단추로 클릭하고 **새 데이터베이스 역할**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="d2c31-133">Right-click **Database Roles**, and select **New Database Role**.</span></span> <span data-ttu-id="d2c31-134">일반 페이지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="d2c31-134">The General page appears.</span></span>

8.  <span data-ttu-id="d2c31-135">**역할 이름**에을 입력 `RSExecRole` 합니다.</span><span class="sxs-lookup"><span data-stu-id="d2c31-135">In **Role name**, type `RSExecRole`.</span></span>

9. <span data-ttu-id="d2c31-136">**소유자**에 **DBO**를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="d2c31-136">In **Owner**, type **DBO**.</span></span>

10. <span data-ttu-id="d2c31-137">**보안 개체**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d2c31-137">Click **Securables**.</span></span>

11. <span data-ttu-id="d2c31-138">**검색**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d2c31-138">Click **Search**.</span></span> <span data-ttu-id="d2c31-139">**개체 추가** 대화 상자가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="d2c31-139">The **Add Objects** dialog box appears.</span></span> <span data-ttu-id="d2c31-140">기본적으로 **특정 개체** 옵션이 선택되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d2c31-140">The **Specific Objects** option is selected by default.</span></span>

12. <span data-ttu-id="d2c31-141">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d2c31-141">Click **OK**.</span></span> <span data-ttu-id="d2c31-142">**개체 선택** 대화 상자가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="d2c31-142">The **Select Objects** dialog box appears.</span></span>

13. <span data-ttu-id="d2c31-143">**개체 유형**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d2c31-143">Click **Object Types**.</span></span>

14. <span data-ttu-id="d2c31-144">**확장 저장 프로시저**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d2c31-144">Click **Extended Stored Procedures**.</span></span>

15. <span data-ttu-id="d2c31-145">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d2c31-145">Click **OK**.</span></span>

16. <span data-ttu-id="d2c31-146">**찾아보기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d2c31-146">Click **Browse**.</span></span>

17. <span data-ttu-id="d2c31-147">확장 저장 프로시저 목록을 아래로 스크롤하여 다음을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="d2c31-147">Scroll down the list of extended stored procedures and select the following:</span></span>

    1.  <span data-ttu-id="d2c31-148">xp_sqlagent_enum_jobs</span><span class="sxs-lookup"><span data-stu-id="d2c31-148">xp_sqlagent_enum_jobs</span></span>

    2.  <span data-ttu-id="d2c31-149">xp_sqlagent_is_starting</span><span class="sxs-lookup"><span data-stu-id="d2c31-149">xp_sqlagent_is_starting</span></span>

    3.  <span data-ttu-id="d2c31-150">xp_sqlagent_notify</span><span class="sxs-lookup"><span data-stu-id="d2c31-150">xp_sqlagent_notify</span></span>

18. <span data-ttu-id="d2c31-151">**확인**을 클릭하고 **확인** 한번 더 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d2c31-151">Click **OK**, and the click **OK** again.</span></span>

19. <span data-ttu-id="d2c31-152">**Execute** 행의 **허용** 열에서 확인란을 클릭한 다음 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d2c31-152">In the **Execute** row, in the **Grant** column, click the check box, and then click **OK**.</span></span>

20. <span data-ttu-id="d2c31-153">나머지 저장 프로시저 각각에 대해 반복합니다.</span><span class="sxs-lookup"><span data-stu-id="d2c31-153">Repeat for each of the remaining stored procedures.</span></span> <span data-ttu-id="d2c31-154">3개의 저장 프로시저 모두에 대해 `RSExecRole`에 Execute 권한을 부여해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d2c31-154">`RSExecRole` must be granted Execute permissions for all three stored procedures.</span></span>

 <span data-ttu-id="d2c31-155">![데이터베이스 역할 속성 페이지](../media/rsexecroledbproperties.gif "데이터베이스 역할 속성 페이지")</span><span class="sxs-lookup"><span data-stu-id="d2c31-155">![Database Role Properties page](../media/rsexecroledbproperties.gif "Database Role Properties page")</span></span>

## <a name="create-rsexecrole-in-msdb"></a><span data-ttu-id="d2c31-156">MSDB에서 RSExecRole 만들기</span><span class="sxs-lookup"><span data-stu-id="d2c31-156">Create RSExecRole in MSDB</span></span>
 <span data-ttu-id="d2c31-157">Reporting Services는 예약된 작업을 지원하기 위해 SQL Server 에이전트 서비스에 대해 저장 프로시저를 사용하고 시스템 테이블에서 작업 정보를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="d2c31-157">Reporting Services uses stored procedures for SQL Server Agent service and retrieves job information from system tables to support scheduled operations.</span></span> <span data-ttu-id="d2c31-158">다음 단계에서는 해당 프로시저에 대한 Execute 권한과 해당 테이블에 대한 Select 권한을 RSExecRole에 부여하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="d2c31-158">The following steps explain how to grant Execute permissions for the procedures and Select permissions on the tables to the RSExecRole.</span></span>

#### <a name="to-create-rsexecrole-in-the-msdb-system-database"></a><span data-ttu-id="d2c31-159">MSDB 시스템 데이터베이스에서 RSExecRole을 만들려면</span><span class="sxs-lookup"><span data-stu-id="d2c31-159">To create RSExecRole in the MSDB system database</span></span>

1.  <span data-ttu-id="d2c31-160">MSDB에서 저장 프로시저 및 테이블에 대한 사용 권한을 부여하기 위해 유사한 단계를 반복합니다.</span><span class="sxs-lookup"><span data-stu-id="d2c31-160">Repeat similar steps for granting permissions to stored procedures and tables in MSDB.</span></span> <span data-ttu-id="d2c31-161">이 단계를 간소화하려면 저장 프로시저와 테이블을 별도로 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="d2c31-161">To simplify the steps, you will provision the stored procedures and tables separately.</span></span>

2.  <span data-ttu-id="d2c31-162">`MSDB`를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="d2c31-162">Open `MSDB`.</span></span>

3.  <span data-ttu-id="d2c31-163">**보안**을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="d2c31-163">Open **Security**.</span></span>

4.  <span data-ttu-id="d2c31-164">**역할**을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="d2c31-164">Open **Roles**.</span></span>

5.  <span data-ttu-id="d2c31-165">**데이터베이스 역할**을 마우스 오른쪽 단추로 클릭하고 **새 데이터베이스 역할**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="d2c31-165">Right-click **Database Roles**, and select **New Database Role**.</span></span> <span data-ttu-id="d2c31-166">일반 페이지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="d2c31-166">The General page appears.</span></span>

6.  <span data-ttu-id="d2c31-167">역할 이름에을 입력 `RSExecRole` 합니다.</span><span class="sxs-lookup"><span data-stu-id="d2c31-167">In Role name, type `RSExecRole`.</span></span>

7.  <span data-ttu-id="d2c31-168">소유자에 **DBO**를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="d2c31-168">In Owner, type **DBO**.</span></span>

8.  <span data-ttu-id="d2c31-169">**보안 개체**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d2c31-169">Click **Securables**.</span></span>

9. <span data-ttu-id="d2c31-170">**추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d2c31-170">Click **Add**.</span></span> <span data-ttu-id="d2c31-171">**개체 추가** 대화 상자가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="d2c31-171">The **Add Objects** dialog box appears.</span></span> <span data-ttu-id="d2c31-172">기본적으로 **특정 개체** 옵션이 선택되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d2c31-172">The **Specify Objects** option is selected by default.</span></span>

10. <span data-ttu-id="d2c31-173">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d2c31-173">Click **OK**.</span></span>

11. <span data-ttu-id="d2c31-174">**개체 유형**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d2c31-174">Click **Object Types**.</span></span>

12. <span data-ttu-id="d2c31-175">**저장 프로시저**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d2c31-175">Click **Stored Procedures.**</span></span>

13. <span data-ttu-id="d2c31-176">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d2c31-176">Click **OK**.</span></span>

14. <span data-ttu-id="d2c31-177">**찾아보기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d2c31-177">Click **Browse**.</span></span>

15. <span data-ttu-id="d2c31-178">항목 목록을 아래로 스크롤하여 다음을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="d2c31-178">Scroll down the list of items and select the following:</span></span>

    1.  <span data-ttu-id="d2c31-179">sp_add_category</span><span class="sxs-lookup"><span data-stu-id="d2c31-179">sp_add_category</span></span>

    2.  <span data-ttu-id="d2c31-180">sp_add_job</span><span class="sxs-lookup"><span data-stu-id="d2c31-180">sp_add_job</span></span>

    3.  <span data-ttu-id="d2c31-181">sp_add_jobschedule</span><span class="sxs-lookup"><span data-stu-id="d2c31-181">sp_add_jobschedule</span></span>

    4.  <span data-ttu-id="d2c31-182">sp_add_jobserver</span><span class="sxs-lookup"><span data-stu-id="d2c31-182">sp_add_jobserver</span></span>

    5.  <span data-ttu-id="d2c31-183">sp_add_jobstep</span><span class="sxs-lookup"><span data-stu-id="d2c31-183">sp_add_jobstep</span></span>

    6.  <span data-ttu-id="d2c31-184">sp_delete_job</span><span class="sxs-lookup"><span data-stu-id="d2c31-184">sp_delete_job</span></span>

    7.  <span data-ttu-id="d2c31-185">sp_help_category</span><span class="sxs-lookup"><span data-stu-id="d2c31-185">sp_help_category</span></span>

    8.  <span data-ttu-id="d2c31-186">sp_help_job</span><span class="sxs-lookup"><span data-stu-id="d2c31-186">sp_help_job</span></span>

    9. <span data-ttu-id="d2c31-187">sp_help_jobschedule</span><span class="sxs-lookup"><span data-stu-id="d2c31-187">sp_help_jobschedule</span></span>

    10. <span data-ttu-id="d2c31-188">sp_verify_job_identifiers</span><span class="sxs-lookup"><span data-stu-id="d2c31-188">sp_verify_job_identifiers</span></span>

16. <span data-ttu-id="d2c31-189">**확인**을 클릭하고 **확인** 한번 더 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d2c31-189">Click **OK**, and the click **OK** again.</span></span>

17. <span data-ttu-id="d2c31-190">첫 번째 저장 프로시저인 sp_add_category를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="d2c31-190">Select the first stored procedure: sp_add_category.</span></span>

18. <span data-ttu-id="d2c31-191">**Execute** 행의 **허용** 열에서 확인란을 클릭한 다음 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d2c31-191">In the **Execute** row, in the **Grant** column, click the checkbox, and then click **OK**.</span></span>

19. <span data-ttu-id="d2c31-192">나머지 저장 프로시저 각각에 대해 반복합니다.</span><span class="sxs-lookup"><span data-stu-id="d2c31-192">Repeat for each of the remaining stored procedures.</span></span> <span data-ttu-id="d2c31-193">10개의 저장 프로시저 모두에 대해 RSExecRole에 Execute 권한을 부여해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d2c31-193">RSExecRole must be granted Execute permissions for all ten stored procedures.</span></span>

20. <span data-ttu-id="d2c31-194">보안 개체 탭에서 **추가** 를 다시 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d2c31-194">On the Securables tab, and click **Add** again.</span></span> <span data-ttu-id="d2c31-195">**개체 추가** 대화 상자가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="d2c31-195">The **Add Objects** dialog box appears.</span></span> <span data-ttu-id="d2c31-196">기본적으로 **특정 개체** 옵션이 선택되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d2c31-196">The **Specify Objects** option is selected by default.</span></span>

21. <span data-ttu-id="d2c31-197">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d2c31-197">Click **OK**.</span></span>

22. <span data-ttu-id="d2c31-198">**개체 유형**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d2c31-198">Click **Object Types**.</span></span>

23. <span data-ttu-id="d2c31-199">**테이블**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d2c31-199">Click **Tables.**</span></span>

24. <span data-ttu-id="d2c31-200">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d2c31-200">Click **OK**.</span></span>

25. <span data-ttu-id="d2c31-201">**찾아보기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d2c31-201">Click **Browse**.</span></span>

26. <span data-ttu-id="d2c31-202">항목 목록을 아래로 스크롤하여 다음을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="d2c31-202">Scroll down the list of items and select the following:</span></span>

    1.  <span data-ttu-id="d2c31-203">syscategories</span><span class="sxs-lookup"><span data-stu-id="d2c31-203">syscategories</span></span>

    2.  <span data-ttu-id="d2c31-204">sysjobs</span><span class="sxs-lookup"><span data-stu-id="d2c31-204">sysjobs</span></span>

27. <span data-ttu-id="d2c31-205">**확인**을 클릭하고 **확인** 한번 더 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d2c31-205">Click **OK**, and the click **OK** again.</span></span>

28. <span data-ttu-id="d2c31-206">첫 번째 테이블인 syscategories를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="d2c31-206">Select the first table: syscategories.</span></span>

29. <span data-ttu-id="d2c31-207">**Select** 행의 **허용** 열에서 확인란을 클릭한 다음 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d2c31-207">In the **Select** row, in the **Grant** column, click the checkbox, and then click **OK**.</span></span>

30. <span data-ttu-id="d2c31-208">sysjobs 테이블에 대해 반복합니다.</span><span class="sxs-lookup"><span data-stu-id="d2c31-208">Repeat for the sysjobs table.</span></span> <span data-ttu-id="d2c31-209">두 테이블 모두에 대해 RSExecRole에 Select 권한을 부여해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d2c31-209">RSExecRole must be granted Select permissions for both tables.</span></span>

## <a name="move-the-report-server-database"></a><span data-ttu-id="d2c31-210">보고서 서버 데이터베이스 이동</span><span class="sxs-lookup"><span data-stu-id="d2c31-210">Move the Report Server Database</span></span>
 <span data-ttu-id="d2c31-211">역할을 만든 후에는 보고서 서버 데이터베이스를 새 SQL Server 인스턴스로 이동할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d2c31-211">After you create the roles, you can move the report server database to new SQL Server instance.</span></span> <span data-ttu-id="d2c31-212">자세한 내용은 [다른 컴퓨터로 보고서 서버 데이터베이스 이동&#40;SSRS 기본 모드&#41;](../report-server/moving-the-report-server-databases-to-another-computer-ssrs-native-mode.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d2c31-212">For more information, see [Moving the Report Server Databases to Another Computer &#40;SSRS Native Mode&#41;](../report-server/moving-the-report-server-databases-to-another-computer-ssrs-native-mode.md).</span></span>

 <span data-ttu-id="d2c31-213">[!INCLUDE[ssDE](../../../includes/ssde-md.md)] 을 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]로 업그레이드하는 경우 데이터베이스를 이동하기 전이나 후에 데이터베이스 엔진을 업그레이드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d2c31-213">If you are upgrading the [!INCLUDE[ssDE](../../../includes/ssde-md.md)] to [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)], you can upgrade it before or after moving the database.</span></span>

 <span data-ttu-id="d2c31-214">보고서 서버 데이터베이스는 보고서 서버를 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] 에 연결할 때 해당 버전으로 자동 업그레이드됩니다.</span><span class="sxs-lookup"><span data-stu-id="d2c31-214">The report server database will be upgraded to the [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] automatically when the report server connects to it.</span></span> <span data-ttu-id="d2c31-215">데이터베이스를 업그레이드하는 데 필요한 특별한 단계는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="d2c31-215">There are no specific steps required for upgrading the database.</span></span>

## <a name="restore-encryption-keys-and-verify-your-work"></a><span data-ttu-id="d2c31-216">암호화 키 복원 및 작업 확인</span><span class="sxs-lookup"><span data-stu-id="d2c31-216">Restore Encryption Keys and Verify Your Work</span></span>
 <span data-ttu-id="d2c31-217">보고서 서버 데이터베이스를 연결한 후에는 다음 단계를 완료하여 작업을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d2c31-217">If you have attached the report server databases, you should now be able to complete the following steps to verify your work.</span></span>

#### <a name="to-verify-report-server-operability-after-a-database-move"></a><span data-ttu-id="d2c31-218">데이터베이스 이동 후 보고서 서버가 작동하는지 확인하려면</span><span class="sxs-lookup"><span data-stu-id="d2c31-218">To verify report server operability after a database move</span></span>

1.  <span data-ttu-id="d2c31-219">Reporting Services 구성 도구를 시작한 후 보고서 서버에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="d2c31-219">Start the Reporting Services Configuration tool and connect to the report server.</span></span>

2.  <span data-ttu-id="d2c31-220">**데이터베이스**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d2c31-220">Click **Database**.</span></span>

3.  <span data-ttu-id="d2c31-221">**데이터베이스 변경**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d2c31-221">Click **Change Database**.</span></span>

4.  <span data-ttu-id="d2c31-222">**기존 보고서 서버 데이터베이스 선택**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d2c31-222">Click **Choose an existing report server database**.</span></span>

5.  <span data-ttu-id="d2c31-223">데이터베이스 엔진의 서버 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="d2c31-223">Enter the server name of the Database Engine.</span></span> <span data-ttu-id="d2c31-224">보고서 서버 데이터베이스를 명명 된 인스턴스에 연결한 경우 인스턴스 이름을 \<servername> \\<instancename 형식으로 입력 해야 \> 합니다.</span><span class="sxs-lookup"><span data-stu-id="d2c31-224">If you attached the report server databases to a named instance, you must type the instance name in this format: \<servername>\\<instancename\>.</span></span>

6.  <span data-ttu-id="d2c31-225">**연결 테스트**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d2c31-225">Click **Test Connection**.</span></span>

7.  <span data-ttu-id="d2c31-226">**다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d2c31-226">Click **Next**.</span></span>

8.  <span data-ttu-id="d2c31-227">데이터베이스에서 보고서 서버 데이터베이스를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="d2c31-227">On the Database, select the report server database.</span></span>

9. <span data-ttu-id="d2c31-228">**다음** 을 클릭하여 마법사를 완료합니다.</span><span class="sxs-lookup"><span data-stu-id="d2c31-228">Click **Next** and complete the wizard.</span></span>

10. <span data-ttu-id="d2c31-229">**암호화 키**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d2c31-229">Click **Encryption Keys**.</span></span>

11. <span data-ttu-id="d2c31-230">**복원**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="d2c31-230">Click **Restore**.</span></span>

12. <span data-ttu-id="d2c31-231">보고서 서버 데이터베이스의 저장된 자격 증명 및 연결 정보를 해독하는 데 사용되는 대칭 키의 백업 복사본이 있는 강력한 파일(.snk)을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="d2c31-231">Select the strong file (.snk) that has the backup copy of the symmetric key used to decrypt stored credentials and connection information in the report server database.</span></span>

13. <span data-ttu-id="d2c31-232">암호를 입력하고 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d2c31-232">Enter the password and click **OK**.</span></span>

14. <span data-ttu-id="d2c31-233">**보고서 관리자 URL**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d2c31-233">Click **Report Manager URL**.</span></span>

15. <span data-ttu-id="d2c31-234">링크를 클릭하여 보고서 관리자를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="d2c31-234">Click the link to open Report Manager.</span></span> <span data-ttu-id="d2c31-235">보고서 서버 데이터베이스의 보고서 서버 항목이 표시되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d2c31-235">You should see the report server items from the report server database.</span></span>

## <a name="see-also"></a><span data-ttu-id="d2c31-236">참고 항목</span><span class="sxs-lookup"><span data-stu-id="d2c31-236">See Also</span></span>
 <span data-ttu-id="d2c31-237">[다른 컴퓨터로 보고서 서버 데이터베이스 이동](../report-server/moving-the-report-server-databases-to-another-computer-ssrs-native-mode.md) [Reporting Services 구성 관리자 &#40;기본](../../sql-server/install/reporting-services-configuration-manager-native-mode.md) 모드&#41;[기본 모드 보고서 서버 데이터베이스 만들기&#41;ssrs &#40;](../install-windows/ssrs-report-server-create-a-native-mode-report-server-database.md) Configuration Manager [암호화 키 백업 및 복원](../install-windows/ssrs-encryption-keys-back-up-and-restore-encryption-keys.md) &#40;</span><span class="sxs-lookup"><span data-stu-id="d2c31-237">[Moving the Report Server Databases to Another Computer &#40;SSRS Native Mode&#41;](../report-server/moving-the-report-server-databases-to-another-computer-ssrs-native-mode.md) [Reporting Services Configuration Manager &#40;Native Mode&#41;](../../sql-server/install/reporting-services-configuration-manager-native-mode.md) [Create a Native Mode Report Server Database  &#40;SSRS Configuration Manager&#41;](../install-windows/ssrs-report-server-create-a-native-mode-report-server-database.md) [Back Up and Restore Reporting Services Encryption Keys](../install-windows/ssrs-encryption-keys-back-up-and-restore-encryption-keys.md)</span></span>


