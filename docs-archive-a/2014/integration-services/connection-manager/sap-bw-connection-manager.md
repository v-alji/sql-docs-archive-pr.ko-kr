---
title: SAP BW 연결 관리자 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 06b166a1-a9df-48ea-a0e8-9b8d6979c0a1
author: chugugrace
ms.author: chugu
ms.openlocfilehash: bc3bb32c4895c6ec8fbcf31d57e8685c74de32dd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647808"
---
# <a name="sap-bw-connection-manager"></a><span data-ttu-id="e4247-102">SAP BW 연결 관리자</span><span class="sxs-lookup"><span data-stu-id="e4247-102">SAP BW Connection Manager</span></span>
  <span data-ttu-id="e4247-103">SAP BW 연결 관리자는 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 for SAP BW의 연결 관리자 구성 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="e4247-103">The SAP BW connection manager is the connection manager component of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 for SAP BW.</span></span> <span data-ttu-id="e4247-104">따라서 SAP BW 연결 관리자는 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 for SAP BW의 원본 및 대상 구성 요소에 필요한 SAP Netweaver BW 버전 7 시스템에 대한 연결을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="e4247-104">Thus, the SAP BW connection manager provides the connectivity to an SAP Netweaver BW version 7 system that the source and destination components of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 for SAP BW need.</span></span> <span data-ttu-id="e4247-105">[!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 for SAP BW 패키지의 일부인 SAP BW 원본 및 대상은 SAP BW 연결 관리자를 사용하는 유일한 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 구성 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="e4247-105">(The SAP BW source and destination that are part of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 for SAP BW package are the only [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] components that use the SAP BW connection manager.)</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="e4247-106">SAP BW용 Microsoft Connector 1.1 설명서는 SAP Netweaver BW 환경에 익숙한 것으로 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="e4247-106">The documentation for the Microsoft Connector 1.1 for SAP BW assumes familiarity with the SAP Netweaver BW environment.</span></span> <span data-ttu-id="e4247-107">SAP Netweaver BW 또는 SAP Netweaver BW 개체 및 프로세스 구성 방법에 대한 자세한 내용은 SAP 설명서를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="e4247-107">For more information about SAP Netweaver BW, or for information about how to configure SAP Netweaver BW objects and processes, see your SAP documentation.</span></span>  
  
 <span data-ttu-id="e4247-108">SAP BW 연결 관리자를 패키지에 추가하면 연결 관리자의 `ConnectionManagerType` 속성이 `SAPBI`로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="e4247-108">When you add an SAP BW connection manager to a package, the `ConnectionManagerType` property of the connection manager is set to `SAPBI`.</span></span>  
  
## <a name="configuring-the-sap-bw-connection-manager"></a><span data-ttu-id="e4247-109">SAP BW 연결 관리자 구성</span><span class="sxs-lookup"><span data-stu-id="e4247-109">Configuring the SAP BW Connection Manager</span></span>  
 <span data-ttu-id="e4247-110">다음과 같은 방법으로 SAP BW 연결 관리자를 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e4247-110">You can configure the SAP BW connection manager in the following ways:</span></span>  
  
-   <span data-ttu-id="e4247-111">연결에 대한 클라이언트, 사용자 이름, 암호 및 언어를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="e4247-111">Provide the client, user name, password, and language for the connection.</span></span>  
  
-   <span data-ttu-id="e4247-112">단일 애플리케이션 서버에 연결할지 아니면 부하 분산 서버의 그룹에 연결할지를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="e4247-112">Choose whether to connect to a single application server or to a group of load-balanced servers.</span></span>  
  
-   <span data-ttu-id="e4247-113">단일 애플리케이션 서버의 호스트 및 시스템 번호를 제공하거나 부하 분산 서버 그룹의 메시지 서버, 그룹 및 SID를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="e4247-113">Provide the host and system number for a single application server, or provide the message server, group, and SID for a group of load-balanced servers.</span></span>  
  
-   <span data-ttu-id="e4247-114">[!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 for SAP BW의 구성 요소에 대한 RFC 함수 호출의 사용자 지정 로깅을 사용하도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="e4247-114">Enable custom logging of RFC function calls for the components of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 for SAP BW.</span></span> <span data-ttu-id="e4247-115">이 로깅은 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 패키지에서 사용하도록 설정할 수 있는 선택적 로깅과 별개입니다. RFC 함수 호출의 로깅을 사용하도록 설정하려면 각 RFC 함수 호출 전후에 생성되는 로그 파일을 저장할 디렉터리를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="e4247-115">(This logging is separate from the optional logging that you can enable on [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] packages.) To enable logging of RFC function calls, you specify a directory in which to store the log files that are created before and after each RFC function call.</span></span> <span data-ttu-id="e4247-116">이 로깅 기능을 사용하면 XML 형식의 로그 파일이 많이 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="e4247-116">(This logging feature creates many log files in XML format.</span></span> <span data-ttu-id="e4247-117">로그 파일에는 전송되는 모든 데이터 행도 포함되므로 많은 디스크 공간이 소비될 수 있습니다. 로그 디렉터리를 선택하지 않으면 로깅이 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e4247-117">As these log files also contain all the rows of data that are transferred, these log files may consume a large amount of disk space.) If you do not select a log directory, logging is not enabled.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="e4247-118">전송되는 데이터에 중요한 정보가 포함되어 있는 경우 로그 파일에도 해당 정보가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="e4247-118">If the data that is transferred contains sensitive information, the log files will also contain that sensitive information.</span></span>  
  
-   <span data-ttu-id="e4247-119">입력한 값을 사용하여 연결을 테스트합니다.</span><span class="sxs-lookup"><span data-stu-id="e4247-119">Use the values that you have entered to test the connection.</span></span>  
  
 <span data-ttu-id="e4247-120">연결 관리자를 구성하는 데 필요한 값 중 모르는 것이 있으면 SAP 관리자에게 문의하십시오.</span><span class="sxs-lookup"><span data-stu-id="e4247-120">If you do not know all the values that are required to configure the connection manager, you might have to ask your SAP administrator.</span></span>  
  
 <span data-ttu-id="e4247-121">SAP BW 연결 관리자, 원본 및 대상을 구성하고 사용하는 방법을 제시하는 연습은 [SAP BI 7.0에서 SQL Server 2008 Integration Services 사용](https://go.microsoft.com/fwlink/?LinkID=137090)백서를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="e4247-121">For a walkthrough that demonstrates how to configure and use the SAP BW connection manager, source, and destination, see the white paper, [Using SQL Server 2008 Integration Services with SAP BI 7.0](https://go.microsoft.com/fwlink/?LinkID=137090).</span></span> <span data-ttu-id="e4247-122">또한 이 백서는 SAP BW에 필요한 개체를 구성하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="e4247-122">This white paper also shows how to configure the required objects in SAP BW.</span></span>  
  
### <a name="using-the-ssis-designer-to-configure-the-source"></a><span data-ttu-id="e4247-123">SSIS 디자이너를 사용하여 원본 구성</span><span class="sxs-lookup"><span data-stu-id="e4247-123">Using the SSIS Designer to Configure the Source</span></span>  
 <span data-ttu-id="e4247-124">[!INCLUDE[ssIS](../../includes/ssis-md.md)] 디자이너에서 설정할 수 있는 SAP BW 연결 관리자의 속성에 대한 자세한 내용을 보려면 다음 항목을 클릭하십시오.</span><span class="sxs-lookup"><span data-stu-id="e4247-124">For more information about the properties of the SAP BW connection manager that you can set in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, click the following topic:</span></span>  
  
-   [<span data-ttu-id="e4247-125">SAP BW 연결 관리자 편집기</span><span class="sxs-lookup"><span data-stu-id="e4247-125">SAP BW Connection Manager Editor</span></span>](../sap-bw-connection-manager-editor.md)  
  
## <a name="see-also"></a><span data-ttu-id="e4247-126">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e4247-126">See Also</span></span>  
 [<span data-ttu-id="e4247-127">Microsoft Connector 1.1 for SAP BW 구성 요소</span><span class="sxs-lookup"><span data-stu-id="e4247-127">Microsoft Connector 1.1 for SAP BW Components</span></span>](../microsoft-connector-for-sap-bw-components.md)  
  
  
