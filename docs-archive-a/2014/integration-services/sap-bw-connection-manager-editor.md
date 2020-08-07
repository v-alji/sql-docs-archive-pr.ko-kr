---
title: 연결 관리자 편집기 SAP BW | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: ec970319-e749-4753-8675-9cf76ed99669
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 527af979fc9c92062f24e1fe161b93e88ed4ab4a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87730831"
---
# <a name="sap-bw-connection-manager-editor"></a><span data-ttu-id="a3ef2-102">SAP BW 연결 관리자 편집기</span><span class="sxs-lookup"><span data-stu-id="a3ef2-102">SAP BW Connection Manager Editor</span></span>
  <span data-ttu-id="a3ef2-103">**SAP BW 연결 관리자 편집기** 를 사용하여 SAP Netweaver BW 버전 7 시스템에 연결하는 데 사용할 속성을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a3ef2-103">Use the **SAP BW Connection Manager Editor** to specify the properties to use to connect to an SAP Netweaver BW version 7 system.</span></span>  
  
 <span data-ttu-id="a3ef2-104">SAP BW 연결 관리자는 SAP 원본 또는 대상에서 SAP Netweaver BW 7 시스템에 연결할 수 있도록 해 줍니다.</span><span class="sxs-lookup"><span data-stu-id="a3ef2-104">The SAP BW connection manager provides connectivity to an SAP Netweaver BW 7 system for use by the SAP BW source or destination.</span></span> <span data-ttu-id="a3ef2-105">[!INCLUDE[msCoName](../includes/msconame-md.md)] Connector 1.1 for SAP BW의 SAP BW 연결 관리자에 대한 자세한 내용은 [SAP BW 연결 관리자](connection-manager/sap-bw-connection-manager.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a3ef2-105">To learn more about the SAP BW connection manager of the [!INCLUDE[msCoName](../includes/msconame-md.md)] Connector 1.1 for SAP BW, see [SAP BW Connection Manager](connection-manager/sap-bw-connection-manager.md).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="a3ef2-106">SAP BW용 Microsoft Connector 1.1 설명서는 SAP Netweaver BW 환경에 익숙한 것으로 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="a3ef2-106">The documentation for the Microsoft Connector 1.1 for SAP BW assumes familiarity with the SAP Netweaver BW environment.</span></span> <span data-ttu-id="a3ef2-107">SAP Netweaver BW 또는 SAP Netweaver BW 개체 및 프로세스 구성 방법에 대한 자세한 내용은 SAP 설명서를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="a3ef2-107">For more information about SAP Netweaver BW, or for information about how to configure SAP Netweaver BW objects and processes, see your SAP documentation.</span></span>  
  
 <span data-ttu-id="a3ef2-108">**SAP BW 연결 관리자 편집기를 열려면**</span><span class="sxs-lookup"><span data-stu-id="a3ef2-108">**To open the SAP BW Connection Manager Editor**</span></span>  
  
1.  <span data-ttu-id="a3ef2-109">[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]에서 SAP BW 연결 관리자가 포함된 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 패키지를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="a3ef2-109">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] package that contains the SAP BW connection manager.</span></span>  
  
2.  <span data-ttu-id="a3ef2-110">**제어 흐름** 탭의 연결 관리자 영역에서 다음 단계 중 하나를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="a3ef2-110">In the Connection Managers area on the **Control Flow** tab, do one of the following steps:</span></span>  
  
    -   <span data-ttu-id="a3ef2-111">SAP BW 연결 관리자를 두 번 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a3ef2-111">Double-click the SAP BW connection manager.</span></span>  
  
         <span data-ttu-id="a3ef2-112">또는</span><span class="sxs-lookup"><span data-stu-id="a3ef2-112">-or-</span></span>  
  
    -   <span data-ttu-id="a3ef2-113">SAP BW 연결 관리자를 마우스 오른쪽 단추로 클릭한 다음 **편집**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="a3ef2-113">Right-click the SAP BW connection manager, and then select **Edit**.</span></span>  
  
## <a name="options"></a><span data-ttu-id="a3ef2-114">옵션</span><span class="sxs-lookup"><span data-stu-id="a3ef2-114">Options</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a3ef2-115">연결 관리자를 구성하는 데 필요한 값 중 모르는 것이 있으면 SAP 관리자에게 문의하십시오.</span><span class="sxs-lookup"><span data-stu-id="a3ef2-115">If you do not know all the values that are required to configure the connection manager, you might have to ask your SAP administrator.</span></span>  
  
 <span data-ttu-id="a3ef2-116">**클라이언트**</span><span class="sxs-lookup"><span data-stu-id="a3ef2-116">**Client**</span></span>  
 <span data-ttu-id="a3ef2-117">시스템의 클라이언트 번호를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="a3ef2-117">Specify the client number of the system.</span></span>  
  
 <span data-ttu-id="a3ef2-118">**언어**</span><span class="sxs-lookup"><span data-stu-id="a3ef2-118">**Language**</span></span>  
 <span data-ttu-id="a3ef2-119">시스템에서 사용하는 언어를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="a3ef2-119">Specify the language that the system uses.</span></span> <span data-ttu-id="a3ef2-120">예를 들어, 영어의 경우 **EN** 을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="a3ef2-120">For example, specify **EN** for English.</span></span>  
  
 <span data-ttu-id="a3ef2-121">**사용자 이름**</span><span class="sxs-lookup"><span data-stu-id="a3ef2-121">**User name**</span></span>  
 <span data-ttu-id="a3ef2-122">시스템에 연결하는 데 사용할 사용자 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="a3ef2-122">Specify the user name that will be used to connect to the system.</span></span>  
  
 <span data-ttu-id="a3ef2-123">**암호**</span><span class="sxs-lookup"><span data-stu-id="a3ef2-123">**Password**</span></span>  
 <span data-ttu-id="a3ef2-124">사용자 이름에 사용할 암호를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="a3ef2-124">Specify the password that will be used with the user name.</span></span>  
  
 <span data-ttu-id="a3ef2-125">**단일 애플리케이션 서버 사용**</span><span class="sxs-lookup"><span data-stu-id="a3ef2-125">**Use single application server**</span></span>  
 <span data-ttu-id="a3ef2-126">단일 애플리케이션 서버에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="a3ef2-126">Connect to a single application server.</span></span>  
  
 <span data-ttu-id="a3ef2-127">부하 분산 서버 그룹에 연결하려면 **부하 분산 사용** 옵션을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="a3ef2-127">To connect to a group of load-balanced servers, use the **Use load balancing** option instead.</span></span>  
  
 <span data-ttu-id="a3ef2-128">**Host**</span><span class="sxs-lookup"><span data-stu-id="a3ef2-128">**Host**</span></span>  
 <span data-ttu-id="a3ef2-129">단일 애플리케이션 서버에 연결하는 경우 호스트 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="a3ef2-129">If connecting to a single application server, specify the host name.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a3ef2-130">이 옵션은 **단일 애플리케이션 서버 사용** 옵션을 선택한 경우에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a3ef2-130">This option is only available if you have selected the **Use single application server** option.</span></span>  
  
 <span data-ttu-id="a3ef2-131">**시스템 번호**</span><span class="sxs-lookup"><span data-stu-id="a3ef2-131">**System number**</span></span>  
 <span data-ttu-id="a3ef2-132">단일 애플리케이션 서버에 연결하는 경우 시스템 번호를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="a3ef2-132">If connecting to a single application server, specify the system number.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a3ef2-133">이 옵션은 **단일 애플리케이션 서버 사용** 옵션을 선택한 경우에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a3ef2-133">This option is only available if you have selected the **Use single application server** option.</span></span>  
  
 <span data-ttu-id="a3ef2-134">**부하 분산 사용**</span><span class="sxs-lookup"><span data-stu-id="a3ef2-134">**Use load balancing**</span></span>  
 <span data-ttu-id="a3ef2-135">부하 분산된 서버 그룹에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="a3ef2-135">Connect to a group of load-balanced servers.</span></span>  
  
 <span data-ttu-id="a3ef2-136">단일 애플리케이션 서버에 연결하려면 **단일 애플리케이션 서버 사용** 옵션을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="a3ef2-136">To connect to a single application server, use the **Use single application server** option instead.</span></span>  
  
 <span data-ttu-id="a3ef2-137">**메시지 서버**</span><span class="sxs-lookup"><span data-stu-id="a3ef2-137">**Message server**</span></span>  
 <span data-ttu-id="a3ef2-138">부하 분산된 서버 그룹에 연결하는 경우 메시지 서버의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="a3ef2-138">If connecting to a group of load-balanced servers, specify the name of the message server.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a3ef2-139">이 옵션은 **부하 분산 사용** 옵션을 선택한 경우에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a3ef2-139">This option is only available if you have selected the **Use load balancing** option.</span></span>  
  
 <span data-ttu-id="a3ef2-140">**그룹**</span><span class="sxs-lookup"><span data-stu-id="a3ef2-140">**Group**</span></span>  
 <span data-ttu-id="a3ef2-141">부하 분산된 서버 그룹에 연결하는 경우 서버 그룹 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="a3ef2-141">If connecting to a group of load-balanced servers, specify the name of the server group name.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a3ef2-142">이 옵션은 **부하 분산 사용** 옵션을 선택한 경우에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a3ef2-142">This option is only available if you have selected the **Use load balancing** option.</span></span>  
  
 <span data-ttu-id="a3ef2-143">**S**</span><span class="sxs-lookup"><span data-stu-id="a3ef2-143">**SID**</span></span>  
 <span data-ttu-id="a3ef2-144">부하 분산된 서버 그룹에 연결하는 경우 연결에 대한 시스템 ID를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="a3ef2-144">If connecting to a group of load-balanced servers, specify the System ID for the connection.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a3ef2-145">이 옵션은 **부하 분산 사용** 옵션을 선택한 경우에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a3ef2-145">This option is only available if you have selected the **Use load balancing** option.</span></span>  
  
 <span data-ttu-id="a3ef2-146">**로그 디렉터리**</span><span class="sxs-lookup"><span data-stu-id="a3ef2-146">**Log directory**</span></span>  
 <span data-ttu-id="a3ef2-147">[!INCLUDE[msCoName](../includes/msconame-md.md)] Connector 1.1 for SAP BW의 구성 요소에 대한 로깅을 사용하도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="a3ef2-147">Enable logging for the components of the [!INCLUDE[msCoName](../includes/msconame-md.md)] Connector 1.1 for SAP BW.</span></span>  
  
 <span data-ttu-id="a3ef2-148">로깅을 사용하도록 설정하려면 각 RFC 함수 호출 전후에 생성되는 로그 파일에 대한 디렉터리를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="a3ef2-148">To enable logging, specify a directory for the log files that are created before and after each RFC function call.</span></span> <span data-ttu-id="a3ef2-149">이 로깅 기능을 사용하면 XML 형식의 로그 파일이 많이 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="a3ef2-149">(This logging feature creates many log files in XML format.</span></span> <span data-ttu-id="a3ef2-150">로그 파일에는 전송되는 모든 데이터 행도 포함되므로 많은 디스크 공간이 소비될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a3ef2-150">As these log files also contain all the rows of data that are transferred, these log files may consume a large amount of disk space.)</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="a3ef2-151">전송되는 데이터에 중요한 정보가 포함되어 있는 경우 로그 파일에도 해당 정보가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="a3ef2-151">If the data that is transferred contains sensitive information, the log files will also contain that sensitive information.</span></span>  
  
 <span data-ttu-id="a3ef2-152">로그 디렉터리를 지정하려면 디렉터리 경로를 수동으로 입력하거나 **찾아보기** 를 클릭하여 로그 디렉터리를 찾아봅니다.</span><span class="sxs-lookup"><span data-stu-id="a3ef2-152">To specify the log directory, you can either enter the directory path manually, or click **Browse** and browse to the log directory.</span></span>  
  
 <span data-ttu-id="a3ef2-153">로그 디렉터리를 선택하지 않으면 로깅이 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a3ef2-153">If you do not select a log directory, logging is not enabled.</span></span>  
  
 <span data-ttu-id="a3ef2-154">**찾아보기**</span><span class="sxs-lookup"><span data-stu-id="a3ef2-154">**Browse**</span></span>  
 <span data-ttu-id="a3ef2-155">로그 디렉터리로 사용할 폴더를 찾아봅니다.</span><span class="sxs-lookup"><span data-stu-id="a3ef2-155">Browse to select a folder for the log directory.</span></span>  
  
 <span data-ttu-id="a3ef2-156">**연결 테스트**</span><span class="sxs-lookup"><span data-stu-id="a3ef2-156">**Test Connection**</span></span>  
 <span data-ttu-id="a3ef2-157">사용자가 제공한 값을 사용하여 연결을 테스트합니다.</span><span class="sxs-lookup"><span data-stu-id="a3ef2-157">Test the connection using the values that you have provided.</span></span> <span data-ttu-id="a3ef2-158">**연결 테스트**를 클릭하면 메시지 상자가 표시되고 연결이 성공했는지 여부가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="a3ef2-158">After clicking **Test Connection**, a message box appears and indicates whether the connection succeeded or failed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a3ef2-159">참고 항목</span><span class="sxs-lookup"><span data-stu-id="a3ef2-159">See Also</span></span>  
 [<span data-ttu-id="a3ef2-160">Microsoft Connector 1.1 for SAP BW F1 도움말</span><span class="sxs-lookup"><span data-stu-id="a3ef2-160">Microsoft Connector 1.1 for SAP BW F1 Help</span></span>](microsoft-connector-for-sap-bw-f1-help.md)  
  
  
