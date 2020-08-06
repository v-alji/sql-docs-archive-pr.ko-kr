---
title: 대상 선택(SQL Server 가져오기 및 내보내기 마법사) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.impexpwizard.chooseadestination.f1
ms.assetid: 1898be15-3e69-42d3-8ecb-3733c9f6c8e3
author: chugugrace
ms.author: chugu
ms.openlocfilehash: e4bf9b717ef9de20d84d32c18eb3caa4c54cad87
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652942"
---
# <a name="choose-a-destination-sql-server-import-and-export-wizard"></a><span data-ttu-id="2fcf3-102">대상 선택(SQL Server 가져오기 및 내보내기 마법사)</span><span class="sxs-lookup"><span data-stu-id="2fcf3-102">Choose a Destination (SQL Server Import and Export Wizard)</span></span>
  <span data-ttu-id="2fcf3-103">**대상 선택** 페이지를 사용하여 복사할 데이터의 대상을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2fcf3-103">Use the **Choose a Destination** page to specify the destination of the data that you want to copy.</span></span>  
  
 <span data-ttu-id="2fcf3-104">이 마법사에 대해 자세히 알아보려면 [SQL Server 가져오기 및 내보내기 마법사](import-and-export-data-with-the-sql-server-import-and-export-wizard.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="2fcf3-104">To learn more about this wizard, see [SQL Server Import and Export Wizard](import-and-export-data-with-the-sql-server-import-and-export-wizard.md).</span></span> <span data-ttu-id="2fcf3-105">마법사 시작 옵션 및 마법사를 성공적으로 실행 하는 데 필요한 사용 권한에 대 한 자세한 내용은 [SQL Server 가져오기 및 내보내기 마법사 실행](start-the-sql-server-import-and-export-wizard.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="2fcf3-105">To learn about the options for starting the wizard, as well as the permissions required to run the wizard successfully, see [Run the SQL Server Import and Export Wizard](start-the-sql-server-import-and-export-wizard.md).</span></span>  
  
 <span data-ttu-id="2fcf3-106">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 가져오기 및 내보내기 마법사는 원본에서 대상으로 데이터를 복사할 목적으로 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="2fcf3-106">The purpose of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Import and Export Wizard is to copy data from a source to a destination.</span></span> <span data-ttu-id="2fcf3-107">이 마법사는 대상 데이터베이스 및 대상 테이블도 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2fcf3-107">The wizard can also create a destination database and destination tables for you.</span></span> <span data-ttu-id="2fcf3-108">그러나 여러 개의 데이터베이스 또는 테이블을 복사하거나 다른 종류의 데이터베이스 개체를 복사할 경우 대신 데이터베이스 복사 마법사를 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2fcf3-108">However, if you have to copy multiple databases or tables, or other kinds of database objects, you should use the Copy Database Wizard instead.</span></span> <span data-ttu-id="2fcf3-109">자세한 내용은 [Use the Copy Database Wizard](../../relational-databases/databases/use-the-copy-database-wizard.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="2fcf3-109">For more information, see [Use the Copy Database Wizard](../../relational-databases/databases/use-the-copy-database-wizard.md).</span></span>  
  
## <a name="static-options"></a><span data-ttu-id="2fcf3-110">정적 옵션</span><span class="sxs-lookup"><span data-stu-id="2fcf3-110">Static Options</span></span>  
 <span data-ttu-id="2fcf3-111">**대상**</span><span class="sxs-lookup"><span data-stu-id="2fcf3-111">**Destination**</span></span>  
 <span data-ttu-id="2fcf3-112">대상의 데이터 스토리지 형식과 일치하는 데이터 공급자를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="2fcf3-112">Choose the data provider that matches the data storage format of the destination.</span></span> <span data-ttu-id="2fcf3-113">데이터 원본에 사용할 수 있는 공급자가 여러 개 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2fcf3-113">There may be more than one provider available for your data source.</span></span> <span data-ttu-id="2fcf3-114">예를 들어 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에서는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client, .Net Framework Data Provider for SQL Server 또는 Microsoft OLE DB Provider for SQL Server를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2fcf3-114">For example, with [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] you can use [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client, the .NET Framework Data Provider for SQL Server, or the Microsoft OLE DB Provider for SQL Server.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="2fcf3-115">ODBC 대상에 데이터를 저장하려면 .NET Framework Data Provider for ODBC를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="2fcf3-115">To save data to an ODBC destination, select the .NET Framework Data Provider for ODBC.</span></span>  
  
 <span data-ttu-id="2fcf3-116">**데이터 원본** 속성의 옵션은 컴퓨터에 설치된 공급자에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="2fcf3-116">The **Data Source** property has a variable number of options, which change depending on the providers installed on the computer.</span></span> <span data-ttu-id="2fcf3-117">다음 표에서는 일반적으로 사용하는 몇 가지 대상에 대한 옵션을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="2fcf3-117">The following tables list the options for some commonly used destinations.</span></span> <span data-ttu-id="2fcf3-118">다른 공급자에 대한 내용은 공급자 설명서를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="2fcf3-118">For other providers, see the provider-specific documentation.</span></span>  
  
## <a name="dynamic-options"></a><span data-ttu-id="2fcf3-119">동적 옵션</span><span class="sxs-lookup"><span data-stu-id="2fcf3-119">Dynamic Options</span></span>  
 <span data-ttu-id="2fcf3-120">다음 섹션에서는 여러 개의 데이터 원본에 사용 가능한 옵션을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="2fcf3-120">The following sections show the options available for several data sources.</span></span> <span data-ttu-id="2fcf3-121">대상 드롭다운 목록에서 사용 가능한 대상 중 일부는 여기에 나열되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="2fcf3-121">Not all the destinations that are available in the Destination drop-down are listed here.</span></span>  
  
### <a name="destination--sql-server-native-client-or-microsoft-ole-db-provider-for-sql-server"></a><span data-ttu-id="2fcf3-122">대상 = SQL Server Native Client 또는 Microsoft OLE DB Provider for SQL Server</span><span class="sxs-lookup"><span data-stu-id="2fcf3-122">Destination = SQL Server Native Client or Microsoft OLE DB Provider for SQL Server</span></span>  
 <span data-ttu-id="2fcf3-123">**서버 이름**</span><span class="sxs-lookup"><span data-stu-id="2fcf3-123">**Server name**</span></span>  
 <span data-ttu-id="2fcf3-124">데이터를 받을 서버 이름을 입력하거나 목록에서 서버를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="2fcf3-124">Type the name of the server to receive the data, or choose a server from the list.</span></span>  
  
 <span data-ttu-id="2fcf3-125">**Windows 인증 사용**</span><span class="sxs-lookup"><span data-stu-id="2fcf3-125">**Use Windows Authentication**</span></span>  
 <span data-ttu-id="2fcf3-126">패키지에서 Microsoft Windows 인증을 사용하여 데이터베이스에 로그인해야 하는지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="2fcf3-126">Specify whether the package should use Microsoft Windows Authentication to log in to the database.</span></span> <span data-ttu-id="2fcf3-127">보안을 강화하려면 Windows 인증을 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="2fcf3-127">Windows Authentication is recommended for better security.</span></span>  
  
 <span data-ttu-id="2fcf3-128">**SQL Server 인증 사용**</span><span class="sxs-lookup"><span data-stu-id="2fcf3-128">**Use SQL Server Authentication**</span></span>  
 <span data-ttu-id="2fcf3-129">패키지에서 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인증을 사용하여 데이터베이스에 로그인할지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="2fcf3-129">Specify whether the package should use [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication to log in to the database.</span></span> <span data-ttu-id="2fcf3-130">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인증을 사용하는 경우 사용자 이름과 암호를 입력해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2fcf3-130">If you use [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication, you must provide a user name and password.</span></span>  
  
 <span data-ttu-id="2fcf3-131">**사용자 이름**</span><span class="sxs-lookup"><span data-stu-id="2fcf3-131">**User name**</span></span>  
 <span data-ttu-id="2fcf3-132">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인증을 사용하는 경우 데이터베이스 연결에 대한 사용자 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="2fcf3-132">Specify a user name for the database connection when you are using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication.</span></span>  
  
 <span data-ttu-id="2fcf3-133">**암호**</span><span class="sxs-lookup"><span data-stu-id="2fcf3-133">**Password**</span></span>  
 <span data-ttu-id="2fcf3-134">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인증을 사용하는 경우 데이터베이스 연결에 대한 암호를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="2fcf3-134">Provide the password for the database connection when you are using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication.</span></span>  
  
 <span data-ttu-id="2fcf3-135">**Database**</span><span class="sxs-lookup"><span data-stu-id="2fcf3-135">**Database**</span></span>  
 <span data-ttu-id="2fcf3-136">지정한 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]인스턴스의 데이터베이스 목록에서 선택하거나 **새로 만들기**단추를 클릭하여 새 데이터베이스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="2fcf3-136">Select from the list of databases on the specified instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], or create a new database by clicking **New**.</span></span>  
  
 <span data-ttu-id="2fcf3-137">**새로 고침**</span><span class="sxs-lookup"><span data-stu-id="2fcf3-137">**Refresh**</span></span>  
 <span data-ttu-id="2fcf3-138">**새로 고침**을 클릭하여 사용 가능한 데이터베이스 목록을 복원합니다.</span><span class="sxs-lookup"><span data-stu-id="2fcf3-138">Restore the list of available databases by clicking **Refresh**.</span></span>  
  
 <span data-ttu-id="2fcf3-139">**새로 만들기**</span><span class="sxs-lookup"><span data-stu-id="2fcf3-139">**New**</span></span>  
 <span data-ttu-id="2fcf3-140">**데이터베이스 만들기** 대화 상자를 사용하여 새 대상 데이터베이스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="2fcf3-140">Create a new destination database by using the **Create Database** dialog box.</span></span>  
  
### <a name="destination--flat-file-destination"></a><span data-ttu-id="2fcf3-141">대상 = 플랫 파일 대상</span><span class="sxs-lookup"><span data-stu-id="2fcf3-141">Destination = Flat File Destination</span></span>  
 <span data-ttu-id="2fcf3-142">**파일 이름**</span><span class="sxs-lookup"><span data-stu-id="2fcf3-142">**File name**</span></span>  
 <span data-ttu-id="2fcf3-143">데이터를 저장할 파일의 경로 및 파일 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="2fcf3-143">Specify the path and file name for the file in which to store the data.</span></span> <span data-ttu-id="2fcf3-144">또는 **찾아보기** 를 클릭하여 파일을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="2fcf3-144">Or, click **Browse** to locate a file.</span></span>  
  
 <span data-ttu-id="2fcf3-145">**찾아보기**</span><span class="sxs-lookup"><span data-stu-id="2fcf3-145">**Browse**</span></span>  
 <span data-ttu-id="2fcf3-146">**열기** 대화 상자를 사용하여 파일을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="2fcf3-146">Locate a file by using the **Open** dialog box.</span></span>  
  
 <span data-ttu-id="2fcf3-147">**로캘**</span><span class="sxs-lookup"><span data-stu-id="2fcf3-147">**Locale**</span></span>  
 <span data-ttu-id="2fcf3-148">문자 정렬 순서와 날짜 및 시간 형식을 정의하는 로캘 ID(LCID)를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="2fcf3-148">Specify the locale ID (LCID) that defines character sort orders and date and time formatting.</span></span>  
  
 <span data-ttu-id="2fcf3-149">**유니코드**</span><span class="sxs-lookup"><span data-stu-id="2fcf3-149">**Unicode**</span></span>  
 <span data-ttu-id="2fcf3-150">유니코드를 사용할지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="2fcf3-150">Indicate whether to use Unicode.</span></span> <span data-ttu-id="2fcf3-151">유니코드를 사용하면 코드 페이지를 지정할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="2fcf3-151">If you use Unicode, you do not have to specify a code page.</span></span>  
  
 <span data-ttu-id="2fcf3-152">**코드 페이지**</span><span class="sxs-lookup"><span data-stu-id="2fcf3-152">**Code page**</span></span>  
 <span data-ttu-id="2fcf3-153">사용할 언어의 코드 페이지를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="2fcf3-153">Specify the code page for the language you want to use.</span></span>  
  
 <span data-ttu-id="2fcf3-154">**형식**</span><span class="sxs-lookup"><span data-stu-id="2fcf3-154">**Format**</span></span>  
 <span data-ttu-id="2fcf3-155">구분 기호로 분리됨, 고정 폭, 왼쪽 정렬 중 어떤 서식을 사용할지를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="2fcf3-155">Indicate whether to use delimited, fixed width, or ragged right formatting.</span></span>  
  
|<span data-ttu-id="2fcf3-156">값</span><span class="sxs-lookup"><span data-stu-id="2fcf3-156">Value</span></span>|<span data-ttu-id="2fcf3-157">Description</span><span class="sxs-lookup"><span data-stu-id="2fcf3-157">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="2fcf3-158">구분됨</span><span class="sxs-lookup"><span data-stu-id="2fcf3-158">Delimited</span></span>|<span data-ttu-id="2fcf3-159">**열** 페이지에 지정된 구분 기호로 열을 구분합니다.</span><span class="sxs-lookup"><span data-stu-id="2fcf3-159">Columns are separated by a delimiter, specified on the **Columns** page.</span></span>|  
|<span data-ttu-id="2fcf3-160">고정 폭</span><span class="sxs-lookup"><span data-stu-id="2fcf3-160">Fixed width</span></span>|<span data-ttu-id="2fcf3-161">열에 고정 폭이 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="2fcf3-161">Columns have a fixed width.</span></span>|  
|<span data-ttu-id="2fcf3-162">왼쪽 정렬</span><span class="sxs-lookup"><span data-stu-id="2fcf3-162">Ragged right</span></span>|<span data-ttu-id="2fcf3-163">왼쪽 정렬 파일은 마지막 열을 제외한 모든 열에 고정 폭이 지정된 파일입니다. 마지막 열은 행 구분 기호로 구분됩니다.</span><span class="sxs-lookup"><span data-stu-id="2fcf3-163">Ragged right files are files in which every column has a fixed width, except for the last column, which is delimited by the row delimiter.</span></span>|  
  
 <span data-ttu-id="2fcf3-164">**텍스트 한정자**</span><span class="sxs-lookup"><span data-stu-id="2fcf3-164">**Text qualifier**</span></span>  
 <span data-ttu-id="2fcf3-165">사용할 텍스트 한정자를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="2fcf3-165">Type the text qualifier to use.</span></span> <span data-ttu-id="2fcf3-166">예를 들어 각 텍스트 열을 따옴표로 묶도록 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2fcf3-166">For example, you can specify that each text column be surrounded with quotation marks.</span></span>  
  
 <span data-ttu-id="2fcf3-167">**첫 번째 데이터 행의 열 이름**</span><span class="sxs-lookup"><span data-stu-id="2fcf3-167">**Column names in first data row**</span></span>  
 <span data-ttu-id="2fcf3-168">첫 번째 데이터 행에 열 이름을 표시할지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="2fcf3-168">Indicate whether you want to display column names in the first data row.</span></span>  
  
### <a name="destination--microsoft-excel"></a><span data-ttu-id="2fcf3-169">대상 = Microsoft Excel</span><span class="sxs-lookup"><span data-stu-id="2fcf3-169">Destination = Microsoft Excel</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="2fcf3-170">Excel 2003 또는 이전 버전을 사용하는 데이터 원본에 연결하려는 경우에만 **Microsoft Excel** 을 선택하십시오.</span><span class="sxs-lookup"><span data-stu-id="2fcf3-170">Select **Microsoft Excel** only if you want to connect to a data source that uses Excel 2003 or earlier.</span></span> <span data-ttu-id="2fcf3-171">Excel 2007를 사용 하는 데이터 원본에 연결 하려면 **Microsoft Office 12.0 Access 데이터베이스 엔진 OLE DB 공급자**를 선택 하 **고 속성**을 클릭 한 다음 **데이터 연결 속성** 대화 상자의 **모두** 탭에서 **확장 속성**에을 입력 `Excel 12.0` 합니다.</span><span class="sxs-lookup"><span data-stu-id="2fcf3-171">To connect to a data source that uses Excel 2007, select **Microsoft Office 12.0 Access Database Engine OLE DB Provider**, click **Properties**, and then on the **All** tab of the **Data Link Properties** dialog box, for **Extended Properties**, enter `Excel 12.0`.</span></span>  
  
 <span data-ttu-id="2fcf3-172">**Excel 파일 경로**</span><span class="sxs-lookup"><span data-stu-id="2fcf3-172">**Excel file path**</span></span>  
 <span data-ttu-id="2fcf3-173">데이터를 저장할 통합 문서의 경로 및 파일 이름을 지정 합니다 (예: C:\MyData.xls \\\Sales\Database\Northwind.xls).</span><span class="sxs-lookup"><span data-stu-id="2fcf3-173">Specify the path and file name for the workbook in which to store the data (for example, C:\MyData.xls, \\\Sales\Database\Northwind.xls).</span></span> <span data-ttu-id="2fcf3-174">또는 **찾아보기** 를 클릭하여 통합 문서를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="2fcf3-174">Or, click **Browse** to locate a workbook.</span></span>  
  
 <span data-ttu-id="2fcf3-175">**찾아보기**</span><span class="sxs-lookup"><span data-stu-id="2fcf3-175">**Browse**</span></span>  
 <span data-ttu-id="2fcf3-176">**열기** 대화 상자를 사용하여 Excel 통합 문서를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="2fcf3-176">Locate an Excel workbook by using the **Open** dialog box.</span></span>  
  
 <span data-ttu-id="2fcf3-177">**Excel 버전**</span><span class="sxs-lookup"><span data-stu-id="2fcf3-177">**Excel version**</span></span>  
 <span data-ttu-id="2fcf3-178">대상 통합 문서에서 사용할 Excel 버전을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="2fcf3-178">Select the version of Excel that is used by the destination workbook.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="2fcf3-179">데이터를 [!INCLUDE[ofprexcel](../../includes/ofprexcel-md.md)] 대상으로 내보낼 때 마법사는 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] Excel 대상 구성 요소를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="2fcf3-179">When you export data to a [!INCLUDE[ofprexcel](../../includes/ofprexcel-md.md)] destination, the wizard uses the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] Excel Destination component.</span></span> <span data-ttu-id="2fcf3-180">몇 가지 사용 시 고려 사항 및 알려진 문제에 대한 자세한 내용은 [Excel Destination](../data-flow/excel-destination.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="2fcf3-180">For information on some usage considerations and known issues, see [Excel Destination](../data-flow/excel-destination.md).</span></span>  
  
### <a name="destination--microsoft-access"></a><span data-ttu-id="2fcf3-181">대상 = Microsoft Access</span><span class="sxs-lookup"><span data-stu-id="2fcf3-181">Destination = Microsoft Access</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="2fcf3-182">Access 2003 또는 이전 버전을 사용하는 데이터베이스에 연결하려는 경우에만 **Microsoft Access** 를 선택하십시오.</span><span class="sxs-lookup"><span data-stu-id="2fcf3-182">Select **Microsoft Access** only if you want to connect to a database that uses Access 2003 or earlier.</span></span> <span data-ttu-id="2fcf3-183">Access 2007을 사용하는 데이터베이스에 연결하려면 **Microsoft Office 12.0 Access Database Engine OLE DB Provider**를 선택하십시오.</span><span class="sxs-lookup"><span data-stu-id="2fcf3-183">To connect to a database that uses Access 2007, select **Microsoft Office 12.0 Access Database Engine OLE DB Provider**.</span></span>  
  
 <span data-ttu-id="2fcf3-184">**파일 이름**</span><span class="sxs-lookup"><span data-stu-id="2fcf3-184">**File name**</span></span>  
 <span data-ttu-id="2fcf3-185">데이터를 저장할 데이터베이스 파일의 경로 및 파일 이름 (예: C:\MyData.mdb, \Sales\Database\Northwind.mdb)을 지정 합니다 \\ .</span><span class="sxs-lookup"><span data-stu-id="2fcf3-185">Specify the path and file name for the database file in which to store the data (for example, C:\MyData.mdb, \\\Sales\Database\Northwind.mdb).</span></span> <span data-ttu-id="2fcf3-186">또는 **찾아보기** 를 클릭하여 데이터베이스 파일을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="2fcf3-186">Or, click **Browse** to locate a database file.</span></span>  
  
 <span data-ttu-id="2fcf3-187">**찾아보기**</span><span class="sxs-lookup"><span data-stu-id="2fcf3-187">**Browse**</span></span>  
 <span data-ttu-id="2fcf3-188">**열기** 대화 상자를 사용하여 해당 데이터베이스 파일을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="2fcf3-188">Browse to the database file by using the **Open** dialog box.</span></span>  
  
 <span data-ttu-id="2fcf3-189">**사용자 이름**</span><span class="sxs-lookup"><span data-stu-id="2fcf3-189">**User name**</span></span>  
 <span data-ttu-id="2fcf3-190">작업 그룹 정보 파일이 데이터베이스에 연결된 경우 데이터베이스 연결에 유효한 사용자 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="2fcf3-190">Specify a valid user name for the database connection when a workgroup information file is associated with the database.</span></span>  
  
 <span data-ttu-id="2fcf3-191">**암호**</span><span class="sxs-lookup"><span data-stu-id="2fcf3-191">**Password**</span></span>  
 <span data-ttu-id="2fcf3-192">작업 그룹 정보 파일이 데이터베이스에 연결된 경우 데이터베이스 연결에 대한 사용자 암호를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="2fcf3-192">Provide the user's password for the database connection when a workgroup information file is associated with the database.</span></span> <span data-ttu-id="2fcf3-193">그러나 모든 사용자에 대해 단일 암호를 사용하여 데이터베이스를 보호하는 경우 **고급** 단추를 클릭하여 액세스하는 **데이터 연결 속성** 대화 상자에서 이 값을 제공해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2fcf3-193">However, if the database is protected with a single password for all users, you must provide this value in the **Data Link Properties** dialog box, which is accessed from the **Advanced** button.</span></span>  
  
 <span data-ttu-id="2fcf3-194">**고급**</span><span class="sxs-lookup"><span data-stu-id="2fcf3-194">**Advanced**</span></span>  
 <span data-ttu-id="2fcf3-195">**데이터 연결 속성** 대화 상자를 사용하여 데이터베이스 암호 또는 기본이 아닌 작업 그룹 정보 파일과 같은 고급 옵션을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="2fcf3-195">Specify advanced options, such as the database password or a non-default workgroup information file, by using the **Data Link Properties** dialog box.</span></span> <span data-ttu-id="2fcf3-196">OLE DB 공급자 속성에 대한 자세한 내용은 [MSDN Library](https://go.microsoft.com/fwlink/?linkid=62553)의 데이터 액세스 섹션을 검색하십시오.</span><span class="sxs-lookup"><span data-stu-id="2fcf3-196">For more information about OLE DB provider properties, search in the Data Access section of the [MSDN Library](https://go.microsoft.com/fwlink/?linkid=62553).</span></span>  
  
  
