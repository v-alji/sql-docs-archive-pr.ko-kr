---
title: 데이터 원본 선택(SQL Server 가져오기 및 내보내기 마법사) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.impexpwizard.chooseadatasource.f1
ms.assetid: ebf28a62-dfc1-4b39-9db5-df1919e5fccb
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 246c3b03bfefad83cbfc1d0110e1fd4cf0cedf7f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652948"
---
# <a name="choose-a-data-source-sql-server-import-and-export-wizard"></a><span data-ttu-id="8db78-102">데이터 원본 선택(SQL Server 가져오기 및 내보내기 마법사)</span><span class="sxs-lookup"><span data-stu-id="8db78-102">Choose a Data Source (SQL Server Import and Export Wizard)</span></span>
  <span data-ttu-id="8db78-103">**데이터 원본 선택** 페이지를 사용 하 여 복사할 데이터의 원본을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8db78-103">Use the **Choose a Data Source** page to specify the source of the data that you want to copy.</span></span>  
  
 <span data-ttu-id="8db78-104">이 마법사에 대해 자세히 알아보려면 [SQL Server 가져오기 및 내보내기 마법사](import-and-export-data-with-the-sql-server-import-and-export-wizard.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="8db78-104">To learn more about this wizard, see [SQL Server Import and Export Wizard](import-and-export-data-with-the-sql-server-import-and-export-wizard.md).</span></span> <span data-ttu-id="8db78-105">마법사 시작 옵션 및 마법사를 성공적으로 실행 하는 데 필요한 권한에 대 한 자세한 내용은 [SQL Server 가져오기 및 내보내기 마법사 실행](start-the-sql-server-import-and-export-wizard.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="8db78-105">To learn about the options for starting the wizard, and about the permissions required to run the wizard successfully, see [Run the SQL Server Import and Export Wizard](start-the-sql-server-import-and-export-wizard.md).</span></span>  
  
 <span data-ttu-id="8db78-106">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 가져오기 및 내보내기 마법사는 원본에서 대상으로 데이터를 복사할 목적으로 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="8db78-106">The purpose of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Import and Export Wizard is to copy data from a source to a destination.</span></span> <span data-ttu-id="8db78-107">이 마법사는 대상 데이터베이스 및 대상 테이블도 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8db78-107">The wizard can also create a destination database and destination tables for you.</span></span> <span data-ttu-id="8db78-108">그러나 여러 개의 데이터베이스 또는 테이블을 복사하거나 다른 종류의 데이터베이스 개체를 복사할 경우 대신 데이터베이스 복사 마법사를 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8db78-108">However, if you have to copy multiple databases or tables, or other kinds of database objects, you should use the Copy Database Wizard instead.</span></span> <span data-ttu-id="8db78-109">자세한 내용은 [Use the Copy Database Wizard](../../relational-databases/databases/use-the-copy-database-wizard.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="8db78-109">For more information, see [Use the Copy Database Wizard](../../relational-databases/databases/use-the-copy-database-wizard.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="8db78-110">옵션</span><span class="sxs-lookup"><span data-stu-id="8db78-110">Options</span></span>  
 <span data-ttu-id="8db78-111">**데이터 원본**</span><span class="sxs-lookup"><span data-stu-id="8db78-111">**Data Source**</span></span>  
 <span data-ttu-id="8db78-112">원본의 데이터 스토리지 형식과 일치하는 데이터 공급자를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="8db78-112">Choose the data provider that matches the data storage format of the source.</span></span> <span data-ttu-id="8db78-113">데이터 원본에 사용할 수 있는 공급자가 여러 개 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8db78-113">There may be more than one provider available for your data source.</span></span> <span data-ttu-id="8db78-114">예를 들어 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에서는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client, .Net Framework Data Provider for SQL Server 또는 Microsoft OLE DB Provider for SQL Server를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8db78-114">For example, with [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] you can use [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client, the .NET Framework Data Provider for SQL Server, or the Microsoft OLE DB Provider for SQL Server.</span></span>  
  
 <span data-ttu-id="8db78-115">**데이터 원본** 속성의 옵션은 컴퓨터에 설치된 공급자에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="8db78-115">The **Data Source** property has a variable number of options, which depend on the providers installed on the computer.</span></span> <span data-ttu-id="8db78-116">다음 표에서는 자주 사용되는 일부 대상에 대한 옵션을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="8db78-116">The following tables list the options for some frequently used destinations.</span></span> <span data-ttu-id="8db78-117">다른 공급자에 대한 내용은 공급자 설명서를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="8db78-117">For other providers, see the provider-specific documentation.</span></span>  
  
## <a name="dynamic-options"></a><span data-ttu-id="8db78-118">동적 옵션</span><span class="sxs-lookup"><span data-stu-id="8db78-118">Dynamic Options</span></span>  
 <span data-ttu-id="8db78-119">다음 섹션에서는 여러 개의 데이터 원본에 사용 가능한 옵션을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="8db78-119">The following sections show the options available for several data sources.</span></span> <span data-ttu-id="8db78-120">대상 드롭다운에서 사용 가능한 모든 대상이 여기에 나열된 것은 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="8db78-120">Not all the data sources that are available in the Data Source drop-down are listed here.</span></span>  
  
### <a name="data-source--sql-server-native-client-and-microsoft-ole-db-provider-for-sql-server"></a><span data-ttu-id="8db78-121">데이터 원본 = SQL Server Native Client 및 Microsoft OLE DB Provider for SQL Server</span><span class="sxs-lookup"><span data-stu-id="8db78-121">Data Source = SQL Server Native Client and Microsoft OLE DB Provider for SQL Server</span></span>  
 <span data-ttu-id="8db78-122">**서버 이름**</span><span class="sxs-lookup"><span data-stu-id="8db78-122">**Server name**</span></span>  
 <span data-ttu-id="8db78-123">데이터가 포함된 서버의 이름을 입력하거나 목록에서 서버를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="8db78-123">Type the name of the server that contains the data, or choose a server from the list.</span></span>  
  
 <span data-ttu-id="8db78-124">**Windows 인증 사용**</span><span class="sxs-lookup"><span data-stu-id="8db78-124">**Use Windows Authentication**</span></span>  
 <span data-ttu-id="8db78-125">패키지에서 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 인증을 사용하여 데이터베이스에 로그인하도록 할지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="8db78-125">Specify whether the package should use [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows Authentication to log in to the database.</span></span> <span data-ttu-id="8db78-126">보안을 강화하려면 Windows 인증을 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="8db78-126">Windows Authentication is recommended for better security.</span></span>  
  
 <span data-ttu-id="8db78-127">**SQL Server 인증 사용**</span><span class="sxs-lookup"><span data-stu-id="8db78-127">**Use SQL Server Authentication**</span></span>  
 <span data-ttu-id="8db78-128">패키지에서 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인증을 사용하여 데이터베이스에 로그인할지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="8db78-128">Specify whether the package should use [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication to log in to the database.</span></span> <span data-ttu-id="8db78-129">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인증을 사용하는 경우 사용자 이름과 암호를 입력해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8db78-129">If you use [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication, you must provide a user name and password.</span></span>  
  
 <span data-ttu-id="8db78-130">**사용자 이름**</span><span class="sxs-lookup"><span data-stu-id="8db78-130">**User name**</span></span>  
 <span data-ttu-id="8db78-131">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인증을 사용하는 경우 데이터베이스 연결에 대한 사용자 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="8db78-131">Specify a user name for the database connection when you are using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication.</span></span>  
  
 <span data-ttu-id="8db78-132">**암호**</span><span class="sxs-lookup"><span data-stu-id="8db78-132">**Password**</span></span>  
 <span data-ttu-id="8db78-133">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인증을 사용하는 경우 데이터베이스 연결에 대한 암호를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="8db78-133">Provide the password for the database connection when you are using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication.</span></span>  
  
 <span data-ttu-id="8db78-134">**Database**</span><span class="sxs-lookup"><span data-stu-id="8db78-134">**Database**</span></span>  
 <span data-ttu-id="8db78-135">지정된 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스에 있는 데이터베이스 목록에서 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="8db78-135">Select from the list of databases on the specified instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="8db78-136">**새로 고침**</span><span class="sxs-lookup"><span data-stu-id="8db78-136">**Refresh**</span></span>  
 <span data-ttu-id="8db78-137">**새로 고침**을 클릭하여 사용 가능한 데이터베이스 목록을 복원합니다.</span><span class="sxs-lookup"><span data-stu-id="8db78-137">Restore the list of available databases by clicking **Refresh**.</span></span>  
  
### <a name="data-source--net-framework-data-provider-for-sql-server"></a><span data-ttu-id="8db78-138">데이터 원본 = .NET Framework Data Provider for SQL Server</span><span class="sxs-lookup"><span data-stu-id="8db78-138">Data Source = .NET Framework Data Provider for SQL Server</span></span>  
 <span data-ttu-id="8db78-139">이 페이지에서는 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] Data Provider for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에 대한 옵션을 사전순으로 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="8db78-139">This page presents an alphabetical list of options for the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] Data Provider for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="8db78-140">다음 표에서는 가장 중요한 옵션을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="8db78-140">The most important options are listed in the following table.</span></span>  
  
 <span data-ttu-id="8db78-141">**데이터 원본**</span><span class="sxs-lookup"><span data-stu-id="8db78-141">**Data Source**</span></span>  
 <span data-ttu-id="8db78-142">데이터가 포함된 서버의 이름을 입력하거나 목록에서 서버를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="8db78-142">Type the name of the server that contains the data, or choose a server from the list.</span></span>  
  
 <span data-ttu-id="8db78-143">**초기 카탈로그**</span><span class="sxs-lookup"><span data-stu-id="8db78-143">**Initial Catalog**</span></span>  
 <span data-ttu-id="8db78-144">원본 데이터베이스의 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="8db78-144">Type the name of the source database.</span></span>  
  
 <span data-ttu-id="8db78-145">**통합 보안**</span><span class="sxs-lookup"><span data-stu-id="8db78-145">**Integrated Security**</span></span>  
 <span data-ttu-id="8db78-146">Windows 통합 인증을 사용하여 연결(권장)하려면 `True`를 지정하고 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인증을 사용하여 연결하려면 `False`를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="8db78-146">Specify `True` to connect by using Windows integrated authentication, which is recommended, or `False` to connect by using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication.</span></span> <span data-ttu-id="8db78-147">`False`를 지정하면 사용자 ID와 암호를 입력해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8db78-147">If you specify `False`, you must enter a user ID and password.</span></span> <span data-ttu-id="8db78-148">기본값은 `False`입니다.</span><span class="sxs-lookup"><span data-stu-id="8db78-148">The default value is `False`.</span></span>  
  
 <span data-ttu-id="8db78-149">**사용자 ID**</span><span class="sxs-lookup"><span data-stu-id="8db78-149">**User ID**</span></span>  
 <span data-ttu-id="8db78-150">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인증을 사용하는 경우 데이터베이스 연결에 대한 사용자 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="8db78-150">Specify a user name for the database connection when you are using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication.</span></span>  
  
 <span data-ttu-id="8db78-151">**암호**</span><span class="sxs-lookup"><span data-stu-id="8db78-151">**Password**</span></span>  
 <span data-ttu-id="8db78-152">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인증을 사용하는 경우 데이터베이스 연결에 대한 암호를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="8db78-152">Provide the password for the database connection when you are using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication.</span></span>  
  
 <span data-ttu-id="8db78-153">이 공급자 선택 시 나열되는 추가 옵션은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 원본 데이터베이스에 성공적으로 연결하기 위해 꼭 필요한 옵션은 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="8db78-153">The additional options that are listed when you select this provider are not required to connect successfully to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] source database.</span></span> <span data-ttu-id="8db78-154">이러한 추가 옵션에 대한 자세한 설명은 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 소프트웨어 개발 키트의 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Data Provider for [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 에 대한 설명서를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="8db78-154">For a description of these additional options, see the documentation for the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] Data Provider for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] Software Development Kit.</span></span>  
  
### <a name="data-source--microsoft-excel"></a><span data-ttu-id="8db78-155">데이터 원본 = Microsoft Excel</span><span class="sxs-lookup"><span data-stu-id="8db78-155">Data Source = Microsoft Excel</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="8db78-156">Excel 2003 또는 이전 버전을 사용하는 데이터 원본에 연결하려는 경우에만 **Microsoft Excel** 을 선택하십시오.</span><span class="sxs-lookup"><span data-stu-id="8db78-156">Select **Microsoft Excel** only if you want to connect to a data source that uses Excel 2003 or earlier.</span></span> <span data-ttu-id="8db78-157">Excel 2007를 사용 하는 데이터 원본에 연결 하려면 **Microsoft Office 12.0 Access 데이터베이스 엔진 OLE DB 공급자**를 선택 하 **고 속성**을 클릭 한 다음 **데이터 연결 속성** 대화 상자의 **모두** 탭에서 `Excel 12.0` **확장 속성**에 대 한 값을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="8db78-157">To connect to a data source that uses Excel 2007, select **Microsoft Office 12.0 Access Database Engine OLE DB Provider**, click **Properties**, and then on the **All** tab of the **Data Link Properties** dialog box, enter `Excel 12.0` as the value for **Extended Properties**.</span></span>  
  
 <span data-ttu-id="8db78-158">**Excel 파일 경로**</span><span class="sxs-lookup"><span data-stu-id="8db78-158">**Excel file path**</span></span>  
 <span data-ttu-id="8db78-159">데이터를 가져올 스프레드시트의 경로 및 파일 이름(예:</span><span class="sxs-lookup"><span data-stu-id="8db78-159">Specify the path and file name for the spreadsheet from which to import the data.</span></span> <span data-ttu-id="8db78-160">예를 들어 **C:\MyData.xls \\\Sales\Database\Northwind.xls**합니다.</span><span class="sxs-lookup"><span data-stu-id="8db78-160">For example, **C:\MyData.xls, \\\Sales\Database\Northwind.xls**.</span></span> <span data-ttu-id="8db78-161">또는 **찾아보기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="8db78-161">Or, click **Browse**.</span></span>  
  
 <span data-ttu-id="8db78-162">**찾아보기**</span><span class="sxs-lookup"><span data-stu-id="8db78-162">**Browse**</span></span>  
 <span data-ttu-id="8db78-163">**열기** 대화 상자를 사용하여 스프레드시트를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="8db78-163">Locate the spreadsheet by using the **Open** dialog box.</span></span>  
  
 <span data-ttu-id="8db78-164">**Excel 버전**</span><span class="sxs-lookup"><span data-stu-id="8db78-164">**Excel version**</span></span>  
 <span data-ttu-id="8db78-165">원본 데이터가 저장된 Excel 버전을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="8db78-165">Select the version of Excel that the source data is stored in.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="8db78-166">데이터를 [!INCLUDE[ofprexcel](../../includes/ofprexcel-md.md)] 원본에서 가져올 때 마법사는 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] Excel 원본 구성 요소를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="8db78-166">When you import data from a [!INCLUDE[ofprexcel](../../includes/ofprexcel-md.md)] source, the wizard uses the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] Excel Source component.</span></span> <span data-ttu-id="8db78-167">사용 시 고려 사항 및 알려진 문제에 대한 자세한 내용은 [Excel Source](../data-flow/excel-source.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="8db78-167">For information about usage considerations and known issues, see [Excel Source](../data-flow/excel-source.md).</span></span>  
  
### <a name="data-source--microsoft-access"></a><span data-ttu-id="8db78-168">데이터 원본 = Microsoft Access</span><span class="sxs-lookup"><span data-stu-id="8db78-168">Data Source = Microsoft Access</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="8db78-169">Access 2003 또는 이전 버전을 사용하는 데이터베이스에 연결하려는 경우에만 **Microsoft Access** 를 선택하십시오.</span><span class="sxs-lookup"><span data-stu-id="8db78-169">Select **Microsoft Access** only if you want to connect to a database that uses Access 2003 or earlier.</span></span> <span data-ttu-id="8db78-170">Access 2007를 사용 하는 데이터베이스에 연결 하려면 대신 **Microsoft Office 12.0 access 데이터베이스 엔진 OLE DB 공급자** 를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="8db78-170">To connect to a database that uses Access 2007, select **Microsoft Office 12.0 Access Database Engine OLE DB Provider** instead.</span></span>  
  
 <span data-ttu-id="8db78-171">**파일 이름**</span><span class="sxs-lookup"><span data-stu-id="8db78-171">**File name**</span></span>  
 <span data-ttu-id="8db78-172">데이터를 가져올 데이터베이스 파일의 경로 및 파일 이름(예:</span><span class="sxs-lookup"><span data-stu-id="8db78-172">Specify the path and file name for the database file from which to import the data.</span></span> <span data-ttu-id="8db78-173">예를 들어 **C:\MyData.mdb, \\\Sales\Database\Northwind.mdb**와 같이 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8db78-173">For example, **C:\MyData.mdb, \\\Sales\Database\Northwind.mdb**.</span></span> <span data-ttu-id="8db78-174">또는 **찾아보기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="8db78-174">Or, click **Browse**.</span></span>  
  
 <span data-ttu-id="8db78-175">**찾아보기**</span><span class="sxs-lookup"><span data-stu-id="8db78-175">**Browse**</span></span>  
 <span data-ttu-id="8db78-176">**열기** 대화 상자를 사용하여 데이터베이스 파일을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="8db78-176">Locate the database file by using the **Open** dialog box.</span></span>  
  
 <span data-ttu-id="8db78-177">**사용자 이름**</span><span class="sxs-lookup"><span data-stu-id="8db78-177">**User name**</span></span>  
 <span data-ttu-id="8db78-178">작업 그룹 정보 파일이 데이터베이스에 연결된 경우 데이터베이스 연결에 유효한 사용자 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="8db78-178">Specify a valid user name for the database connection when a workgroup information file is associated with the database.</span></span>  
  
 <span data-ttu-id="8db78-179">**암호**</span><span class="sxs-lookup"><span data-stu-id="8db78-179">**Password**</span></span>  
 <span data-ttu-id="8db78-180">작업 그룹 정보 파일이 데이터베이스에 연결된 경우 데이터베이스 연결에 대한 사용자 암호를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="8db78-180">Provide the user's password for the database connection when a workgroup information file is associated with the database.</span></span> <span data-ttu-id="8db78-181">그러나 데이터베이스가 모든 사용자에 대해 단일 암호로 보호되는 경우 **고급** 을 클릭하여 액세스할 수 있는 **데이터 연결 속성**대화 상자에 해당 값을 입력해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8db78-181">However, if the database is protected with a single password for all users, you must provide this value in the **Data Link Properties** dialog box, which is accessed by clicking **Advanced**.</span></span>  
  
 <span data-ttu-id="8db78-182">**고급**</span><span class="sxs-lookup"><span data-stu-id="8db78-182">**Advanced**</span></span>  
 <span data-ttu-id="8db78-183">**데이터 연결 속성** 대화 상자를 사용 하 여 데이터베이스 암호 또는 기본이 아닌 작업 그룹 정보 파일과 같은 고급 옵션을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8db78-183">You may want to specify advanced options, such as the database password or a non-default workgroup information file, by using the **Data Link Properties** dialog box.</span></span> <span data-ttu-id="8db78-184">OLE DB 공급자 속성에 대 한 자세한 내용은 [MSDN library](https://go.microsoft.com/fwlink/?linkid=62553)의 데이터 액세스 섹션을 검색 하십시오.</span><span class="sxs-lookup"><span data-stu-id="8db78-184">For more information about OLE DB provider properties, search in the Data Access section of the [MSDN library](https://go.microsoft.com/fwlink/?linkid=62553).</span></span>  
  
### <a name="data-source--flat-file-source"></a><span data-ttu-id="8db78-185">데이터 원본 = 플랫 파일 원본</span><span class="sxs-lookup"><span data-stu-id="8db78-185">Data Source = Flat File Source</span></span>  
 <span data-ttu-id="8db78-186">플랫 파일 데이터 원본 옵션에 대한 자세한 내용은 다음 항목을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="8db78-186">See the following topics for information about the options for a flat file data source.</span></span>  
  
 [<span data-ttu-id="8db78-187">플랫 파일 연결 관리자 편집기&#40;일반 페이지&#41;</span><span class="sxs-lookup"><span data-stu-id="8db78-187">Flat File Connection Manager Editor &#40;General Page&#41;</span></span>](../general-page-of-integration-services-designers-options.md)  
  
 [<span data-ttu-id="8db78-188">플랫 파일 연결 관리자 편집기&#40;열 페이지&#41;</span><span class="sxs-lookup"><span data-stu-id="8db78-188">Flat File Connection Manager Editor &#40;Columns Page&#41;</span></span>](../flat-file-connection-manager-editor-columns-page.md)  
  
 [<span data-ttu-id="8db78-189">플랫 파일 연결 관리자 편집기&#40;고급 페이지&#41;</span><span class="sxs-lookup"><span data-stu-id="8db78-189">Flat File Connection Manager Editor &#40;Advanced Page&#41;</span></span>](../flat-file-connection-manager-editor-advanced-page.md)  
  
 [<span data-ttu-id="8db78-190">플랫 파일 연결 관리자 편집기&#40;미리 보기 페이지&#41;</span><span class="sxs-lookup"><span data-stu-id="8db78-190">Flat File Connection Manager Editor &#40;Preview Page&#41;</span></span>](../flat-file-connection-manager-editor-preview-page.md)  
  
  
