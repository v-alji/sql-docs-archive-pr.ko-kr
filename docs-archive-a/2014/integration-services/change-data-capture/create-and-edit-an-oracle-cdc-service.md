---
title: Oracle CDC Service 만들기 및 편집 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- createSrv
ms.assetid: 10cd612e-d8f1-4af2-97d3-a0c22e1e2326
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 3325e272285895e813f01d50a1c312e75472919b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649135"
---
# <a name="create-and-edit-an-oracle-cdc-service"></a><span data-ttu-id="78dc1-102">Oracle CDC Service 만들기 및 편집</span><span class="sxs-lookup"><span data-stu-id="78dc1-102">Create and Edit an Oracle CDC Service</span></span>
  <span data-ttu-id="78dc1-103">CDC Service 구성 콘솔에서 새 Oracle CDC Windows 서비스를 만들고 편집합니다.</span><span class="sxs-lookup"><span data-stu-id="78dc1-103">You create and edit a new Oracle CDC Windows Service from the CDC Service Configuration Console.</span></span>  
  
 <span data-ttu-id="78dc1-104">새 Oracle CDC Windows 서비스를 만들려면 왼쪽 창에서 **로컬 CDC Service** 를 선택한 다음 **동작** 창에서 **새 서비스** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="78dc1-104">To create a new Oracle CDC Windows service, select **Local CDC Services** from the left pane, then click **New Service** from the **Actions** pane.</span></span> <span data-ttu-id="78dc1-105">**로컬 CDC Service** 를 마우스 오른쪽 단추로 클릭하고 **새 서비스**를 선택할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="78dc1-105">You can also right-click **Local CDC Services** and select **New Service**.</span></span> <span data-ttu-id="78dc1-106">새 Oracle CDC Windows 서비스 대화 상자가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="78dc1-106">The New Oracle CDC Windows Service dialog box opens.</span></span>  
  
 <span data-ttu-id="78dc1-107">**OR**</span><span class="sxs-lookup"><span data-stu-id="78dc1-107">**OR**</span></span>  
  
 <span data-ttu-id="78dc1-108">CDC Service 속성을 편집하려면 속성을 편집할 서비스를 선택하고 **동작** 창에서 **속성** 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="78dc1-108">To edit the CDC service properties, select the service that you want to edit the properties for and click **Properties** from the **Actions** pane.</span></span> <span data-ttu-id="78dc1-109">작업할 서비스를 마우스 오른쪽 단추로 클릭하고 **속성**을 선택할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="78dc1-109">You can also right-click the service you are working with and select **Properties**.</span></span> <span data-ttu-id="78dc1-110">CDC Service 속성 대화 상자가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="78dc1-110">The CDC Service Properties dialog box opens.</span></span>  
  
 <span data-ttu-id="78dc1-111">새 Oracle CDC Windows 서비스 대화 상자 또는 CDC Service 속성 대화 상자에 다음 정보를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="78dc1-111">Enter the following information in the New Oracle CDC Windows Service dialog box or the CDC Service Properties dialog box.</span></span>  
  
 <span data-ttu-id="78dc1-112">서비스 이름</span><span class="sxs-lookup"><span data-stu-id="78dc1-112">Service Name</span></span>  
 <span data-ttu-id="78dc1-113">새 Oracle CDC Windows 서비스의 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="78dc1-113">Type the name of the new Oracle CDC Windows Service.</span></span> <span data-ttu-id="78dc1-114">가급적이면 긴 이름을 사용하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="78dc1-114">You should not use long names, if possible.</span></span> <span data-ttu-id="78dc1-115">/ 및 \ 문자는 서비스 이름에 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="78dc1-115">The characters / and \ cannot be used in the service name.</span></span>  
  
> [!NOTE]  
> <span data-ttu-id="78dc1-116">서비스를 편집하는 경우 이 옵션을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="78dc1-116">This option is not available when editing the service.</span></span> <span data-ttu-id="78dc1-117">이미 존재하는 Windows 서비스의 이름을 변경할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="78dc1-117">You cannot change the name of a Windows service that already exists.</span></span>  
  
 <span data-ttu-id="78dc1-118">**설명**</span><span class="sxs-lookup"><span data-stu-id="78dc1-118">**Description**</span></span>  
 <span data-ttu-id="78dc1-119">식별에 도움이 되도록 서비스에 대한 설명을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="78dc1-119">Type a description of the service to help identify it.</span></span>  
  
 <span data-ttu-id="78dc1-120">**서비스 계정**</span><span class="sxs-lookup"><span data-stu-id="78dc1-120">**Service Account**</span></span>  
 <span data-ttu-id="78dc1-121">다음 중 하나를 선택하여 서비스를 실행할 계정을 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="78dc1-121">Select one of the following to determine under which account to run the service:</span></span>  
  
-   <span data-ttu-id="78dc1-122">**로컬 시스템 계정**</span><span class="sxs-lookup"><span data-stu-id="78dc1-122">**Local System Account**</span></span>  
  
     <span data-ttu-id="78dc1-123">이 옵션은 서비스에 너무 많은 권한을 부여하므로 권장되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="78dc1-123">This is not recommended because it gives too many permissions to the service.</span></span>  
  
-   <span data-ttu-id="78dc1-124">**계정 지정**</span><span class="sxs-lookup"><span data-stu-id="78dc1-124">**This Account**</span></span>  
  
     <span data-ttu-id="78dc1-125">Windows Vista 또는 Windows Server 2008에서 기본 서비스 계정은 네트워크 서비스 계정입니다.</span><span class="sxs-lookup"><span data-stu-id="78dc1-125">On Windows Vista or Windows Server 2008, the default service account is the NETWORK SERVICE account.</span></span>  
  
     <span data-ttu-id="78dc1-126">Windows 7, Windows Server 2008 R2 이상에서 기본 서비스 계정은 NT Service\\<service-name>입니다.</span><span class="sxs-lookup"><span data-stu-id="78dc1-126">On Windows 7, Windows Server 2008 R2 and later, the default service account is NT Service\\<service-name>.</span></span>  
  
     <span data-ttu-id="78dc1-127">이러한 계정에는 암호가 필요 없으므로 이 계정을 사용하면 암호를 사용하지 않고 작업할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="78dc1-127">Using these accounts lets you work without using passwords because a password is not necessary for these accounts.</span></span> <span data-ttu-id="78dc1-128">또한 이러한 계정은 Oracle CDC Service를 실행하는 데 필요한 필수 권한만 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="78dc1-128">In addition these accounts provide only the necessary permissions required for the Oracle CDC Service to run.</span></span>  
  
     <span data-ttu-id="78dc1-129">로컬 또는 도메인 Windows 계정을 서비스 계정에 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="78dc1-129">You can use a local or domain Windows account for the service account.</span></span> <span data-ttu-id="78dc1-130">이 경우 해당 계정의 **암호** 를 입력해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="78dc1-130">In this case, you must enter the **Password** for that account.</span></span> <span data-ttu-id="78dc1-131">이 계정은 로컬 호스트 또는 도메인 계정에 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="78dc1-131">This account can be for the local host or a domain account.</span></span> <span data-ttu-id="78dc1-132">암호를 변경할 경우 Windows 제어판에서 로컬 서비스를 사용하여 암호를 업데이트해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="78dc1-132">Be sure to update the password when it is changed using Local Services in the Windows Control Panel.</span></span>  
  
 <span data-ttu-id="78dc1-133">**서버 이름**: 연결할 대상 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스를 선택합니다(예: **\\\\<computer_name>\\<instance_name>** ).</span><span class="sxs-lookup"><span data-stu-id="78dc1-133">**Server name**: Select the target [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance to connect to (for example, **\\\\<computer_name>\\<instance_name>**).</span></span> <span data-ttu-id="78dc1-134">마지막으로 연결한 서버 인스턴스가 기본적으로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="78dc1-134">The server instance last connected to is displayed by default.</span></span>  
  
 <span data-ttu-id="78dc1-135">**인증**</span><span class="sxs-lookup"><span data-stu-id="78dc1-135">**Authentication**</span></span>  
 <span data-ttu-id="78dc1-136">다음 중 하나를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="78dc1-136">Select one of the following:</span></span>  
  
-   <span data-ttu-id="78dc1-137">**Windows 인증**: 이 옵션을 선택하면 Oracle CDC Service는 서비스 계정 ID를 사용하여 대상 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="78dc1-137">**Windows Authentication**: If you select this option, the Oracle CDC service connects to the target [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance using the service account identity.</span></span> <span data-ttu-id="78dc1-138">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스가 다른 컴퓨터에서 실행 중인 경우 도메인 계정과 함께 Windows 인증을 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="78dc1-138">If the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance is running on a different computer, Windows Authentication must be used with domain accounts.</span></span>  
  
-   <span data-ttu-id="78dc1-139">**SQL Server 인증**: 이 옵션을 선택하면 사용하려는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 로그인의 **사용자 이름**과 **암호**를 입력해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="78dc1-139">**SQL Server Authentication**: If you select this option, you must type the **User Name** and **Password** for the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login you want to use.</span></span> <span data-ttu-id="78dc1-140">Oracle CDC Service는 대상 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스에 연결할 때 이러한 자격 증명을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="78dc1-140">The Oracle CDC service uses these credentials when connecting to the target [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance.</span></span>  
  
 <span data-ttu-id="78dc1-141">Oracle CDC Service에서 사용되는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 로그인은 공용 고정 서버 역할의 구성원이면 가능하며 다른 권한은 필요 없습니다.</span><span class="sxs-lookup"><span data-stu-id="78dc1-141">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login used by the Oracle CDC Service only needs to be a member of the public fixed-server role, no other privileges are needed.</span></span> <span data-ttu-id="78dc1-142">새 Oracle CDC 인스턴스를 추가하면 해당 로그인은 연결된 **CDC 데이터베이스에 대한** db_owner [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 액세스 권한을 얻게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="78dc1-142">Once new Oracle CDC Instances are added, that login will gain **db_owner** access to the associated [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] CDC databases.</span></span>  
  
 <span data-ttu-id="78dc1-143">Oracle CDC Windows 서비스 정의를 만들려면 프로그램은 연결된 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스에서 MSXDBCDC 데이터베이스에 대한 액세스 권한을 업데이트해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="78dc1-143">To create the Oracle CDC Windows Service definition, the program needs update access to the MSXDBCDC database in the associated [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance.</span></span> <span data-ttu-id="78dc1-144">**확인**을 클릭하면 사용자가 MSXDBCDC 데이터베이스의 업데이트 권한이 있는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 로그인을 입력할 수 있는 대화 상자가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="78dc1-144">When you click **OK**, a dialog box prompts the user to enter a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login with an update access to the MSXDBCDC database.</span></span>  
  
 <span data-ttu-id="78dc1-145">SQL Server에 연결 대화 상자에 입력해야 하는 데이터에 대한 자세한 내용은 [Connection to SQL Server](connection-to-sql-server.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="78dc1-145">For information about the data you must type into the Connect to SQL Server dialog box, see [Connection to SQL Server](connection-to-sql-server.md).</span></span>  
  
 <span data-ttu-id="78dc1-146">**옵션**</span><span class="sxs-lookup"><span data-stu-id="78dc1-146">**Options**</span></span>  
 <span data-ttu-id="78dc1-147">화살표를 클릭하면 구성할 수 있는 옵션을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="78dc1-147">Click the arrow to view available options to be configured.</span></span> <span data-ttu-id="78dc1-148">이러한 옵션을 기본값으로 그대로 둘 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="78dc1-148">You can choose to leave these options with their default value.</span></span> <span data-ttu-id="78dc1-149">사용 가능한 옵션은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="78dc1-149">The available options are:</span></span>  
  
-   <span data-ttu-id="78dc1-150">**연결 제한 시간**: 제한 시간이 초과되기 전에 Oracle용 CDC Service가 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에 연결될 때까지 기다리는 시간(초)을 입력합니다. 기본값은 **15**입니다.</span><span class="sxs-lookup"><span data-stu-id="78dc1-150">**Connection Timeout**: Type the time (in seconds) that the CDC Service for Oracle waits for a connection to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] before timing out. The default value is **15**.</span></span>  
  
-   <span data-ttu-id="78dc1-151">**실행 제한 시간**: 제한 시간이 초과되기 전에 Oracle CDC Windows 서비스에서 명령이 실행될 때까지 기다리는 시간(초)을 입력합니다. 기본값은 **30**입니다.</span><span class="sxs-lookup"><span data-stu-id="78dc1-151">**Execution Timeout**: Type the time (in seconds) that the Oracle CDC Windows Service waits for a command to execute before timing out. The default value is **30**.</span></span>  
  
-   <span data-ttu-id="78dc1-152">**연결 암호화**: 암호화된 연결을 사용하는 대상 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스와 Oracle CDC Service 사이의 통신을 위해 **연결 암호화**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="78dc1-152">**Encrypt Connection**: Select **Encrypt Connection** for communication between the Oracle CDC Service and the target [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance using an encrypted connection.</span></span>  
  
-   <span data-ttu-id="78dc1-153">**고급**: 필요한 경우 모든 추가 연결 속성을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="78dc1-153">**Advanced**: Type any additional connection properties, if necessary.</span></span>  
  
 <span data-ttu-id="78dc1-154">**마스터 암호**</span><span class="sxs-lookup"><span data-stu-id="78dc1-154">**Master Password**</span></span>  
 <span data-ttu-id="78dc1-155">Oracle CDC Windows 서비스에서 Oracle 로그 마이닝 자격 증명을 보호하는 데 사용할 암호를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="78dc1-155">Enter a password to be used by the Oracle CDC Windows Service to protect the Oracle log-mining credentials.</span></span>  
  
 <span data-ttu-id="78dc1-156">동일한 서비스의 다른 인스턴스가 고가용성 구성에서 한 클러스터의 다른 노드에 대해 구성된 경우에도 동일한 마스터 암호를 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="78dc1-156">The same master password must also be used when other instances of the same service are configured on other nodes on a cluster in high-availability configuration.</span></span> <span data-ttu-id="78dc1-157">마스터 암호를 잃어버리거나 수정할 경우 CDC Designer 콘솔을 사용하여 Oracle CDC 인스턴스 데이터베이스에 저장된 모든 로그 마이닝 암호를 다시 입력해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="78dc1-157">If you lose or modify the master password, all log mining passwords stored in Oracle CDC Instance databases must be re-entered using the CDC Designer console.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="78dc1-158">참고 항목</span><span class="sxs-lookup"><span data-stu-id="78dc1-158">See Also</span></span>  
 [<span data-ttu-id="78dc1-159">CDC Service를 만들고 편집하는 방법</span><span class="sxs-lookup"><span data-stu-id="78dc1-159">How to Create and Edit a CDC Service</span></span>](how-to-create-and-edit-a-cdc-service.md)  
  
  
